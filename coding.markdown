---
layout: page
title: coding
permalink: /coding/
---
Below you will find code snippets from my previous projects organized by language!

### Python

# Decode string 
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

### Java

# File reading/writing and data processing
{% highlight java %}
public class Evictions
{
    private Town[] towns;
    private double threshold;
    private File inFileName;
    private int CAPACITY = 50;

    public Evictions(File f){
        inFileName = f;
    }

    /**
     * helper method to increase array size
     */    
    private void increaseSize(){
        Town[] temp = new Town[towns.length * 2];
        for (int t = 0; t < towns.length; t++){
            temp[t] = towns[t];
        }
        towns = temp;
    }

    /**
     * reads town data from a txt file and sorts into towns array
     * @param f input file to read data from
     */
    public void readFromFile(File f){
        Town[] towns = new Town[CAPACITY];
        int counter = 0;
        try{
            Scanner scan = new Scanner(f); 
            scan.nextLine(); //skips first line with no data
            int index = 0;
            scan.useDelimiter("\t|\\n"); //Separates the elements on each String

            while (scan.hasNext()) {
                if (counter == towns.length){
                    increaseSize();
                }
                String name = scan.next(); //assigns each element to a parameter in the Town constructor
                String state = scan.next();
                int pop = scan.nextInt();
                double povRate = scan.nextDouble();
                int evictions = scan.nextInt();
                Town t = new Town(name, state, pop, povRate, evictions);
                towns[index] = t;
                index++;
            }
            scan.close();
        }
        catch (FileNotFoundException e){
            System.out.println(e);
        }
        this.towns = towns;
    }

    /**
     * filters towns according to threshold and writes to a new txt file
     * every town with an eviction rate greater than the threshold
     * @param o name of the output file
     */
    public void filterAndWriteToFile(String o){
        threshold = 0.3;

        try{
            PrintWriter writer = new PrintWriter (new File(o));
            for (int i = 0; i < towns.length; i++){

                if(towns[i] != null){ //if town[i] is not empty and it passes the threshold
                    boolean flag = towns[i].setFlag(threshold);
                    if (flag){
                        writer.println(towns[i]);
                    }
                }
            }
            writer.close();
        }
        catch (IOException e){
            System.out.println(e);
        }
    }

    public static void main(String[] args){
        //instantiates file to be read
        File f = new File("smallEvictionData.txt");
        //creates Eviction object
        Evictions e = new Evictions(f);
        System.out.println("Testing readFromFile");
        e.readFromFile(f);
        System.out.println("First town:");
        System.out.println(e.towns[0]);
        System.out.println("Second town:");
        System.out.println(e.towns[1]);
        System.out.println("Third town:");
        System.out.println(e.towns[2]);
        
        //testing filter and write to file
        e.filterAndWriteToFile("Evictions.txt");
    }
}
{% endhighlight %}

# Bounded queue implementation
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

### C#    

{% highlight c# %}

{% endhighlight %}

