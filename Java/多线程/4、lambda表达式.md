## 函数式接口

> 接口中只定义唯一一个抽象接口
>
> 可以使用lambda表达式来创建该接口的对象

**实例**

> Runnable接口

```java
@FunctionalInterface //定义时用@FunctionalInterface注解
public interface Runnable {
    /**
     * When an object implementing interface <code>Runnable</code> is used
     * to create a thread, starting the thread causes the object's
     * <code>run</code> method to be called in that separately executing
     * thread.
     * <p>
     * The general contract of the method <code>run</code> is that it may
     * take any action whatsoever.
     *
     * @see     java.lang.Thread#run()
     */
    public abstract void run();
}
```



## lambda表达式进化过程

**代码实例**

```java
package com.staticproxy;

public class Lambda {

    //3、静态内部类
    static class LambdaClass2 implements LambdaInterface{
        @Override
        public void funTest() {
            System.out.println("lambda 测试 --> 2");
        }
    }
    public static void main(String[] args) {
        LambdaInterface lambdaInterface = new LambdaClass1();
        lambdaInterface.funTest();

        lambdaInterface = new LambdaClass2();
        lambdaInterface.funTest();

        //4、局部内部类
        class LambdaClass3 implements LambdaInterface{
            @Override
            public void funTest() {
                System.out.println("lambda 测试 --> 3");
            }
        }
        lambdaInterface = new LambdaClass3();
        lambdaInterface.funTest();

        //5、匿名内部类，没有类名称，必须借助接口或者父类
        lambdaInterface = new LambdaInterface() {
            @Override
            public void funTest() {
                System.out.println("lambda 测试 --> 4");
            }
        };
        lambdaInterface.funTest();

        //6、lambda简化，接口名与方法名都不使用，要求接口必须是函数式接口
        lambdaInterface = () ->{
            System.out.println("lambda 测试 --> 5");
        };
        lambdaInterface.funTest();

        //7、lambda简化带参
        LambdaInterfaceParam lambdaInterfaceParam = (int a,int b)->{
            System.out.println("参数1->"+a+" 参数2->"+b);
        };
        lambdaInterfaceParam.funTest(3,5);

        /**
         * lambda简化
         */
        //简化参数类型
        //多个参数简化参数类型必须都去掉，不能一个去一个不去
        //多个参数必须加括号
        lambdaInterfaceParam = (a,b)->{
            System.out.println("参数1->"+a+" 参数2->"+b);
        };
        lambdaInterfaceParam.funTest(5,3);
        //简化括号,参数个数为 1 个时可以简化
        LambdaInterfaceParentheses lambdaInterfaceParentheses = a->{
            System.out.println("简化括号参数 -> "+a);
        };
        lambdaInterfaceParentheses.funTest(10);
        //简化花括号,语句为一句时可以简化
        lambdaInterfaceParentheses = a-> System.out.println("简化花括号 -> "+a);
        lambdaInterfaceParentheses.funTest(20);
    }
}
//1、定义一个函数式接口
interface LambdaInterface{
    void funTest();
}
//2、实现类
class LambdaClass1 implements LambdaInterface{
    @Override
    public void funTest() {
        System.out.println("lambda 测试 --> 1");
    }
}
//带参
interface LambdaInterfaceParam{
    void funTest(int a, int b);
}
//简化括号
interface LambdaInterfaceParentheses{
    void  funTest(int a);
}
```



