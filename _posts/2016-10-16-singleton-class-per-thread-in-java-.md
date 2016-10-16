---
layout: post
title: How to create singleton instance per thread in java
---

> In case you are new to the term `singleton design pattern`, It is recommended that, you read [this article](https://www.tutorialspoint.com/java/java_using_singleton.htm) before proceeding further.

By this time I assume you know the basics and usefulness of a singleton design pattern. 

Sometimes we endup in a situation where we can not use the singleton classes in a multiple threaded application. This could be for sevaral reasons like, making use of some data or some instance which are not thread-safe (eg. `HashMap`). 

To create singleton instance per thread, we can make use of a ThreadLocal instance ([java doc](http://docs.oracle.com/javase/7/docs/api/java/lang/ThreadLocal.html)). 

When we invoke `get()` on a ThreadLocal instance, it returns an independently initialized copy of the variable for each thread. ThreadLocal instances are typically private static fields in classes which we wish to make singleton per thread.

Each thread holds an implicit reference to its copy of a thread-local variable as long as the thread is alive and the ThreadLocal instance is accessible; after a thread goes away, all of its copies of thread-local instances are garbage colelcted.
 
## Example 1 - By using static reference of ThreadLocal 

{% highlight java %}
package com.amiyasahu;

public class Singleton {

    /**
     * Private constructor
     */
    private Singleton() {

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
     * 
     * @return
     */
    public static Singleton getInstance() {
        return _threadLocal.get();
    }
}
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

## Example 2 - By using generic factory pattern 

### Step 1 : Create the singleton class
{% highlight java %}
package com.amiyasahu.factory;

public class Singleton {

}
{% endhighlight %}

### Step 2 : Create the interface

{% highlight java %}
package com.amiyasahu.factory;

public interface Factory<T> {
    public T create();
}
{% endhighlight %}

### Step 3 : Create the generic ThreadLocalFactory utility class

Now create the generic ThreadLocalFactory which can convert any `Factory` to a ThreadLocal scope.

{% highlight java %}
package com.amiyasahu.factory;

public class ThreadLocalFactory<T> implements Factory<T> {

    private final ThreadLocal<T> _threadLocal;

    public ThreadLocalFactory(final Factory<T> factory) {
        _threadLocal = new ThreadLocal<T>() {
            @Override
            protected T initialValue() {
                return factory.create();
            }
        };
    }

    @Override
    public T create() {
        return _threadLocal.get();
    }
}
{% endhighlight %}

### Step 4 : Create a singleton factory

{% highlight java %}
package com.amiyasahu.factory;

public class SingletonFactory implements Factory<Singleton> {
    @Override
    public Singleton create() {
        return new Singleton();
    }
}
{% endhighlight %}

### Step 4 : Push the singleton factory to the thread local scope

{% highlight java %}
package com.amiyasahu.factory;

public class ThreadLocalSF {

    private static Factory<Singleton> factory = null;

    public static Singleton getInstance() {

        if (factory == null) {
            SingletonFactory sf = new SingletonFactory();
            factory = new ThreadLocalFactory<>(sf);
        }
        
        return factory.create();
    }

}
{% endhighlight %}

We are done. Now we have created a Thread local singleton factory, which will return unique instance per thread.

Lets write the test method now. 

{% highlight java %}
package com.amiyasahu.factory;

import java.util.Random;

public class ThreadLocalTest extends Thread {

    public void run() {
        Singleton instance1 = ThreadLocalSF.getInstance();
        System.out.println(getThreadName() + instance1);
        sleep(100, 50); // sleep for some time
        Singleton instance2 = ThreadLocalSF.getInstance();
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

Now lets run the test method - 

{% highlight java %}
package com.amiyasahu;

import com.amiyasahu.factory.ThreadLocalTest;

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
{% highlight bash %}
[Thread-0] - com.amiyasahu.factory.Singleton@4afbf04a
[Thread-1] - com.amiyasahu.factory.Singleton@13f6c937
[Thread-2] - com.amiyasahu.factory.Singleton@5b8425b7
[Thread-1] - com.amiyasahu.factory.Singleton@13f6c937
[Thread-1] - Both are equal
[Thread-0] - com.amiyasahu.factory.Singleton@4afbf04a
[Thread-0] - Both are equal
[Thread-2] - com.amiyasahu.factory.Singleton@5b8425b7
[Thread-2] - Both are equal
{% endhighlight %}

This clearly demonstrates creation of unique objects per thread.