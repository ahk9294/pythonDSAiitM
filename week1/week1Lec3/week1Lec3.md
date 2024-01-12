<center>

## Week1 Lecture 3 
#### Prof Madhvan Mukund | Edited by Abhishek verma.

# Python Recap -1

</center>

<hr>

Let us start the study of *Data structures and Algorithms* by recaping the *syntax* and *functionalities* of python.

We will do this with the help of some running examples.

## Computing gcd of two numbers.

<hr>

Consider the problem of computing the **gcd** of two numbers.

###  What is 'gcd'?

**gcd** or *greatest common factor/divisor* also sometimes called the **hcf**.

One of the best thing about the gcd is that **for any given numbers the gcd always exist.**

For eg. in the worst case like that of 46 and 53 where there are no *common factors* the gcd will be 1. 

Because 1 is always available as the common factor for every number. 

Lets write some python functions to calculate the gcd of two numbers in different ways and later on we will disscuss which way is more efficient than the other.

## the gcd1

<hr>

The most illustrative way of calculating gcd of two numbers is:
- *listing* all common factors of both numbers.....
- and then selecting the largest one.

This method can be implemented in python as follows :

```python
def gcd1(m,n) :
    commonFactors =[]   
    '''
    In Python, there is no way in which the python recognizes 'the type' of varialble unless you initialize it. 
    Here by initializing the variable commonFactors=[] we tell the python that it of 'list' type.

    By doing this we are now ready to apply all the methods on 'commonFactors' designed for the list data type in python.
    '''
    for i in range(1,min(m,n)+1) :  # the gcd will be always less than(or equal to) the min among the m and n. (think why)?
        if (m%i==0 and n%i==0) :
            commonFactors.append(i) # collect the common factors of m and n one by one in the sorted order.
    return(commonFactors[-1])       # pull out the largest common factor. This will be te gcd of m and n.
```


Notice that the above algorithm uses the following *facts* and *resources* :

-  **gcd(m,n)<=min(m,n)**. Think why it is true.

- The *Data Structure* that we used here is the *list*.

We can look the above definition **gcd1** as the 'back-end' for computing the gcd of two numbers.

Now let us type the 'front-end' to supply the inputs and see how the algorithm behaves.

```python
print(gcd1(24,53))

output => 1
```
We noticed that the alogorithm works very fine and given the output.

Now let us consider the second approach to calculate the **gcd**.

## the gcd 2

<hr>

In the definition *gcd1* , if we notice carefully it turns out that : 

 if we are just concerned with calculating the '*greatest common factor*', then there is no need to keep track of all the common-factors.

Infact we just need the ' **m**ost **r**ecent **c**ommon **f**actor'.

So we can modify the gcd1 as follows :

```python
def gcd2(m,n) :
    for i in range(1,min(m,n)+1) :  # the list is completely eliminated as we dont need to keep track of all the common factors.
        if (m%i==0 and n%i==0):
            mrcf = i                # update the mrcf variable with most recent common factor.
    return (mrcf)
```

Lets run this gcd2 and see if it works fine or not.....

```python
print(gcd2(24,36))

output => 12
```

Notice that this works fine too.

Now what we are concerned about is :

- how long these two functions take to calculate the gcd ?...
- ....Which one is more Efficient than other in terms of time and resources that they use.... or both uses same time and resources ?.....
- ...are there more good ways to calculate the gcd ? ....

So these are the type of questions that we are going to look at in details in this course. 

Especially we will try to assess how *efficient* are the peices of codes that we write.

In case of above discussed gcd1 and gcd2 can we guess which one is better ?

It turns out that there is not much difference in the efficiency of **gcd1** and **gcd2** ...

..as both of them involves the **for loop that runs the min(m,n) time**

....**so both of the functions takes time proportional to the minimum of m and n wether they do it with the list or without the list.**

<hr>

So notice that although we changed the Datastructure in above methods... in one case we used the **list** and in the other we recorded the most recent factor in a **variable**....the time taken in both the cases fundamentaly doesnot change....it remains proportional to minimum of m and n.

<hr>


So can't we calculate the gcd in more efficient way?

It turns out that there are better ways, We will see then later. For now lets see the other examples. 
