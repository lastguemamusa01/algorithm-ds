# algorithm-ds
algorithm grokking book 101

## 1 Introduction to algorithms

An algorithm is a set of instructions for accomplishing a task.

### Binary search

Binary search is an algorithm; its input is a sorted list of elements (I’ll explain later why it needs to be sorted). If an element you’re looking for is in that list, binary search returns the position where it’s located. Otherwise, binary search returns null.

Eliminate half the numbers every time with binary search.

In general, for any list of n, binary search will take log2 n steps to run in the worst case, whereas simple search will take n steps.

###  Logarithms

You may not remember what logarithms are, but you probably know what exponentials are. log10 100 is like asking, “How many 10s do we multiply together to get 100?” The answer is 2: 10 × 10. So log10 100 = 2. Logs are the flip of exponentials.

![image](https://user-images.githubusercontent.com/25869911/149870006-1ddc051a-baf3-47a9-a2b2-74d9c831b32a.png)


For a list of 8 elements, log 8 == 3, because 2^3 == 8. So for a list of 8 numbers, you would have to check 3 numbers at most. For a list of 1,024 elements, log 1,024 = 10, because 2^10 == 1,024. So for a list of 1,024 numbers, you’d have to check 10 numbers at most.

You just need to know that you can store
a sequence of elements in a row of consecutive buckets called an array.

###  Running time

Any time I talk about an algorithm, I’ll discuss its running time. Generally you want to choose the most efficient algorithm— whether you’re trying to optimize for time or space.

If this is a list of 100 numbers, it takes up to 100 guesses.
If it’s a list of 4 billion numbers, it takes up to 4 billion guesses. So the maximum number of guesses is the same as the size of the list. This is called linear time.

Binary search runs in logarithmic time (or log time, as the natives call it).

###  Big O notation

Big O notation is special notation that tells you how fast an algorithm is.


###  Algorithm running times grow at different rates

Let’s assume it takes 1 millisecond to check one element. With simple search, Bob has to check 100 elements, so the search takes 100 ms to run. On the other hand, he only has to check 7 elements with binary search (log2 100 is roughly 7), so that search takes 7 ms to run. 

The run time for simple search with 1 billion items will be 1 billion ms, which is 11 days! The problem is, the run times for binary search and simple search don’t grow at the same rate.


### Big O establishes a worst-case run time

Simple search still takes O(n) time. In this case, you found what you were looking for instantly. That’s the best-case scenario. But Big O notation is about the worst-case scenario. So you can say that, in the worst case, you’ll have to look at every entry in the phone book once.

Along with the worst-case run time, it’s also important to look at the average-case run time.

### Some common Big O run times

* O(log n), also known as log time. Example: Binary search.
* O(n), also known as linear time. Example: Simple search.
* O(n * log n). Example: A fast sorting algorithm, like quicksort (coming up in chapter 4).
* O(n^2). Example: A slow sorting algorithm, like selection sort (coming up in chapter 2).
* O(n!). Example: A really slow algorithm, like the traveling salesperson (coming up next!).

![image](https://user-images.githubusercontent.com/25869911/149871282-60f1ee75-2ac4-43f6-89aa-a5692474ab54.png)


* Algorithm speed isn’t measured in seconds, but in growth of the number of operations.
* Instead, we talk about how quickly the run time of an algorithm increases as the size of the input increases.
* Run time of algorithms is expressed in Big O notation.
* O(log n) is faster than O(n), but it gets a lot faster as the list of items you’re searching grows.

### The traveling salesperson

![image](https://user-images.githubusercontent.com/25869911/149871614-06b5a25c-4233-48d4-a5db-773e2e9ffab2.png)


In general, for n items, it will take n! (n factorial) operations to compute the result. So this is O(n!) time, or factorial time.

* Binary search is a lot faster than simple search.
* O(log n) is faster than O(n), but it gets a lot faster once the list of items you’re searching through grows.
* Algorithm speed isn’t measured in seconds.
* Algorithm times are measured in terms of growth of an algorithm.
* Algorithm times are written in Big O notation.


