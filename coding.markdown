---
layout: page
title: coding
permalink: /coding/
---

## Python

Decode string 
{% highlight python %}
def decode(encoded):
    digits = reverse(encoded)
    eq = createDict()
    n=0
    decoded = ""
    while n < len(digits):
        part = digits[n:n+2]
        if int(part) > 12:
            print(part)
            decoded += eq.get(part)
            print(eq.get(part))
            n+=2
        else:
            part = digits[n:n+3]
            decoded += eq.get(part)
            n+=3
    return decoded
        
    
def reverse(string):
    n = len(encoded) - 1
    new = ""
    while n >= 0:
        new += encoded[n];
        n-=1
    return new
def createDict():
    acsEq = {}
    n = 65
    acsEq[str(32)] = ' '
    while n < 91:
        for l in string.ascii_uppercase:
            acsEq[str(n)] =  l
            n+=1
    n = 97
    while n < 123:
        for l in string.ascii_lowercase:
            acsEq[str(n)] = l
            n+=1
    return acsEq
{% endhighlight %}

## Java

Bounded queue implementation
{% highlight java %}
public class BoundedQueue<T> extends CircularArrayQueue<T>
{
    private int c; //max capacity


    
    /**
     * constructor for object
     * 
     * @param c the capacity of the bounded queue
    */
    public BoundedQueue(int c){
        super();
        this.c = c;
    }
    
    /**
     * Returns true if bounded queue is at capacity, false otherwise
     * 
     * @return true if the queue is at capacity, false otherwise.
     */
    
    public boolean isFull(){
        return (this.size() == c);
    }
    
    /**
     * Adds the specified element to the rear of the queue
     * 
     * @param element The element to be enqueued into the queue
     */
    public void enqueue(T element) 
    {
        if(isFull()){
            System.out.println("Cannot enqueue");
        }
        else{
            super.enqueue(element);
        }
    }
    /**
     * main method for testing
     */
    public static void main(String[] args){
        System.out.println("Testing constructor");
        BoundedQueue q = new BoundedQueue(2);
        System.out.println(q);
        
        System.out.println("Testing enqueue()");
        q.enqueue("a");
        System.out.println(q);
        q.enqueue("b");
        System.out.println(q);
        
        System.out.println("Testing isFull()");
        System.out.println("Expecting true Got:" + q.isFull());
    }
}
{% endhighlight %}

## C#
{% highlight c# %}

{% endhighlight %}

