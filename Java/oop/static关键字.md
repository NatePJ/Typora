## java中static

> static修饰的属性和方法类加载时加载，属于类，可以使用类名调用静态属性与静态方法

#### 属性



#### 方法

> 静态方法可以调用动态方法，动态方法不能调用静态方法



#### 代码块

> - ==执行顺序==
>   - 先：静态代码块--->动态代码块--->构造方法：后



#### 静态导入包

```java
import static java.lang.Math.random;//random是一个静态方法，可以导入方法，需要加static关键字
import static java.lang.Math.PI;//PI是一个静态属性，同理
public class Demo01 {
    public static void main(String[] args) {
        System.out.println(random());//可以直接使用，不需要类型调用(Math.random())
        System.out.println(PI);//同理，直接使用
    }
}
```





#### 举例 System、Math

> System、Math类构造方法为private，所以不能被实例化。其方法与属性都是static修饰的静态方法和属性，可以直接调用，而不需要实例化

## C语言中static

