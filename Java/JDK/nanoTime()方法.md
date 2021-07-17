==摘抄，有时间自己整理==

# [Java的nanoTime()方法](https://www.cnblogs.com/somefuture/p/13690961.html)

java有两个获取和时间相关的秒数方法，一个是广泛使用的

> System.currentTimeMillis()

返回的是从一个长整型结果，表示毫秒。

另一个是

> System.nanoTime()

返回的是纳秒。

“纳”这个单位 一般不是第一次见。前几年相当火爆的“纳米”和他是同一级别。纳表示的是10的-9次方。在真空中，光一纳秒也只能传播30厘米。

比纳秒大一级别的是微秒，10的-6次方；然后是就是毫秒，10的-3次方。

纳秒下面还有皮秒、飞秒等。

既然纳秒比毫秒高10的6次方精度，那么他们的比值就应该是10的6次方。然而并非如此。

看下面的代码

```java
public static void main(String[] args) {
    long l = System.currentTimeMillis();
    Date date = new Date(l);
    System.out.println(l);
    System.out.println(date);
}
```

最后输出的当前时间。

大家可能都知道毫秒方法返回的是自1970年到现在的毫秒数。而Java的日期也是如此，所以他俩是等值的。

但是使用纳秒方法的输出可能让我们丈二和尚摸不着头脑：

```java
public static void main(String[] args) {
    long l = System.nanoTime();
    Date date = new Date(l / 1_000_000);
    System.out.println(l);
    System.out.println(date);
}
```

这个输出在不同的机器上可能不一样，我的输出是Fri Jan 02 07:58:38 CST 1970

为什么会这样？

根据纳秒方法的注释：

> Returns the current value of the running Java Virtual Machine's high-resolution time source, in nanoseconds.
> This method can only be used to measure elapsed time and is not related to any other notion of system or wall-clock time. The value returned represents nanoseconds since some fixed but arbitrary origin time (perhaps in the future, so values may be negative). The same origin is used by all invocations of this method in an instance of a Java virtual machine; other virtual machine instances are likely to use a different origin.

翻译一下就是：返回当前JVM的高精度时间。该方法只能用来测量时段而和系统时间无关。它的返回值是从某个固定但随意的时间点开始的（可能是未来的某个时间）。不同的JVM使用的起点可能不同。

这样有点恐怖的是我们相同的代码在不同机器运行导致结果可能不同。

所以它很少用来计算。通常都是测量。

下面写一个程序来反映他和毫秒方法的关系。

```java
  Lists.newArrayList(1,2,3,4,5,6,7,8,9).parallelStream().forEach(i -> {
        long m = System.currentTimeMillis();
        long n = System.nanoTime();
        try {
            Thread.sleep(1000);
        } catch (InterruptedException ignored) {
        }
        long m1 = System.currentTimeMillis();
        long n1 = System.nanoTime();
        long m0 = m1 - m;
        long n0 = n1 - n;

        System.out.println(i + " -- " + (n0 / m0));
    });
}
```

输出如下：

```
3 -- 999756
6 -- 1000129
2 -- 999984
4 -- 999868
5 -- 999019
1 -- 999100
8 -- 999768
7 -- 999753
9 -- 1000139
```

不同的测试可能结果不同，不过可以看到，这个比值大约是10的6次方。