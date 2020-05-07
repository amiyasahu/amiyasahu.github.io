---
layout: post
title: How to create singleton instance per thread in java
---

> In case you are new to the term `singleton design pattern`, It is recommended that, you read [this article](https://www.tutorialspoint.com/java/java_using_singleton.htm) before proceeding further.

By this time I assume you know the basics and usefulness of a singleton design pattern. 

Sometimes we endup in a situation where we can not use the singleton classes in a multiple threaded application. This could be for sevaral reasons like, making use of some data or some instance which are not thread-safe (eg. `HashMap`). 

To create singleton instance per thread, we can make use of a ThreadLocal instance ([java doc](http://docs.oracle.com/javase/7/docs/api/java/lang/ThreadLocal.html)). 

When we invoke `get()` on a ThreadLocal instance, it returns an independently initialized copy of the variable for each thread. ThreadLocal instances are typically private static fields in classes which we wish to make singleton per thread.

Each thread holds an implicit reference to its copy of a thread-local variable as long as the thread is alive and the ThreadLocal instance is accessible; after a thread goes away, all of its copies of thread-local instances are garbage collected.

{% highlight java %}
package com.amiyasahu;

public class Singleton {

    private Singleton() {
        // Private constructor
    }

    private static ThreadLocal<Singleton> _threadLocal = 
                new ThreadLocal<Singleton>() {
                    @Override
                    protected Singleton initialValue() {
                        return new Singleton();
                    }
                };

    /**
     * Returns the thread local singleton instance
     */
    public static Singleton getInstance() {
        return _threadLocal.get();
    }
}
{% endhighlight %}

If you are using java8 or above, you can replace the _threadLocal definition with below.

{% highlight java %}

_threadLocal = ThreadLocal.withInitial(() -> new Singleton());
                        
{% endhighlight %}

Now lets create the test method. Here we will print the instance hashcode with the thread name, so that we can conclude which instance is bound for a thread.

{% highlight java %}
package com.amiyasahu;

import java.util.Random;

public class ThreadLocalTest extends Thread {

    public void run() {
        Singleton instance1 = Singleton.getInstance();
        System.out.println(getThreadName() + instance1);
        sleep(100, 50); // sleep for some time
        Singleton instance2 = Singleton.getInstance();
        System.out.println(getThreadName() + instance2);
        boolean equal = instance1 == instance2;
        String message = equal ? "Both are equal" : "Not equal";
        System.out.println(getThreadName() + message);
    }

    private void sleep(int max, int min) {
        try {
            int time = new Random().nextInt(max - min + 1) + min;
            Thread.sleep(time);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
    }

    private String getThreadName() {
        return "[" + Thread.currentThread().getName() + "] - ";
    }

}
{% endhighlight %}

Run the test case -

{% highlight java %}
package com.amiyasahu;

public class App {
    public static void main(String[] args) {
        Thread t1 = new ThreadLocalTest();
        t1.start();
        
        Thread t2 = new ThreadLocalTest();
        t2.start();
        
        Thread t3 = new ThreadLocalTest();
        t3.start();
    }
}
{% endhighlight %}

Output - 
{% highlight shell %}
[Thread-1] - com.amiyasahu.Singleton@7504f8eb
[Thread-2] - com.amiyasahu.Singleton@274b8c21
[Thread-0] - com.amiyasahu.Singleton@50dcdeae
[Thread-1] - com.amiyasahu.Singleton@7504f8eb
[Thread-1] - Both are equal
[Thread-0] - com.amiyasahu.Singleton@50dcdeae
[Thread-0] - Both are equal
[Thread-2] - com.amiyasahu.Singleton@274b8c21
[Thread-2] - Both are equal
{% endhighlight %}

This clearly shows, it is creating a unique instance per thread.
