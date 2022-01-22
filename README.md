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


## 2 Selection Sort

Arrays and linked lists—two of the most basic data structures. They’re used absolutely everywhere. 

You can run binary search only on a sorted list of elements. This chapter teaches you selection sort. Most languages have a sorting algorithm built in, so you’ll rarely need to write your own version from scratch. But selection sort is a stepping stone to quicksort


This is basically how your computer’s memory works. Your computer looks like a giant set of drawers, and each drawer has an address

fe0/ffeeb is the address of a slot in memory.

Each time you want to store an item in memory, you ask the computer for some space, and it gives you an address where you can store your item. If you want to store multiple items, there are two basic ways to do so: arrays and lists.

### Arrays and linked lists

Sometimes you need to store a list of elements in memory. Suppose you’re writing an app to manage your todos. You’ll want to store the todos as a list in memory.
Should you use an array, or a linked list? Let’s store the todos in an array first, because it’s easier to grasp. Using an array means all your tasks are stored contiguously (right next to each other) in memory.

Now suppose you want to add a fourth task. But the next drawer is taken up by someone else’s stuff!

It’s like going to a movie with your friends and finding a place to sit— but another friend joins you, and there’s no place for them. You have to move to a new spot where you all fit. In this case, you need to ask your computer for a different chunk of memory that can fit four tasks. Then you need to move all your tasks there.

Similarly, adding new items to an array can be a big pain. If you’re out of space and need to move to a new spot in memory every time, adding a new item will be really slow.

One easy fix is to “hold seats”: even if you have only 3 items in your task list, you can ask the computer for 10 slots, just in case. Then you can add 10 items to your task list without having to move. This is a good workaround, but you should be aware of a couple of downsides:
• You may not need the extra slots that you asked for, and then that memory will be wasted. You aren’t using it, but no one else can use it either.
• You may add more than 10 items to your task list and have to move anyway.

So it’s a good workaround, but it’s not a perfect solution. Linked lists solve this problem of adding items

### Linked lists

With linked lists, your items can be anywhere in memory.

Each item stores the address of the next item in the list. A bunch of random memory addresses are linked together.

It’s like a treasure hunt. You go to the first address, and it says, “The next item can be found at address 123.” So you go to address 123, and it says, “The next item can be found at address 847,” and so on. Adding an item to a linked list is easy: you stick it anywhere in memory and store the address with the previous item.

With linked lists, you never have to move your items. You also avoid another problem. Let’s say you go to a popular movie with five of your friends. The six of you are trying to find a place to sit, but the theater
is packed. There aren’t six seats together. Well, sometimes this happens with arrays. Let’s say you’re trying to find 10,000 slots for an array. Your memory has 10,000 slots, but it doesn’t have 10,000 slots together. You can’t get space for your array! A linked list is like saying, “Let’s split up and watch the movie.” If there’s space in memory, you have space for your linked list.
If linked lists are so much better at inserts, what are arrays good for?

### Arrays

Websites with top-10 lists use a scummy tactic to get more page views. Instead of showing you the list on one page, they put one item on each page and make you click Next to get to the next item in the list. For example, Top 10 Best TV Villains won’t show you the entire list on one page. Instead, you start at #10 (Newman), and you have to click Next on each page to reach #1 (Gustavo Fring). This technique gives the websites 10 whole pages on which to show you ads, but it’s boring to click Next 9 times to get to #1. It would be much better if the whole list was on one page and you could click each person’s name for more info.

Linked lists have a similar problem. Suppose you want to read the last item in a linked list. You can’t just read it, because you don’t know what address it’s at. Instead, you have to go to item #1 to get the address for item #2. Then you have to go to item #2 to get the address for item #3. And so on, until you get to the last item.Linked lists are great if you’re going to read all the items one at a time: you can read one item, follow the address to the next item, and so on. But if you’re going to keep jumping around, linked lists are terrible.

Arrays are different. You know the address for every item in your array. For example, suppose your array contains five items, and you know it starts at address 00. What is the address of item #5

### Terminology

The elements in an array are numbered. This numbering starts from 0, not 1. For example, in this array, 20 is at position 1.
Almost every programming language you use will number array elements starting at 0. You’ll soon get used to it.
The position of an element is called its index. So instead of saying, “20 is at position 1,” the correct terminology is, “20 is at index 1.”

![image](https://user-images.githubusercontent.com/25869911/150656342-f96d75a2-3c71-459d-a0a6-723fccb8253a.png)


### Inserting into the middle of a list

What’s better if you want to insert elements in the middle: arrays or lists? With lists, it’s as easy as changing what the previous element points to.
But for arrays, you have to shift all the rest of the elements down.
And if there’s no space, you might have to copy everything to a new location! Lists are better if you want to insert elements into the middle.

### Deletions

What if you want to delete an element? Again, lists are better, because you just need to change what the previous element points to. With arrays, everything needs to be moved up when you delete an element.

Unlike insertions, deletions will always work. Insertions can fail sometimes when there’s no space left in memory. But you can always delete an element.


![image](https://user-images.githubusercontent.com/25869911/150656458-e4dbe802-e348-4a9d-95c1-7223bb0f11a4.png)


insertions and deletions are O(1) time only if you can instantly access the element to be deleted. It’s a common practice to keep track of the first and last items in a linked list, so it would take only O(1) time to delete those.

Which are used more: arrays or lists? Obviously, it depends on the use case. But arrays see a lot of use because they allow random access. There are two different types of access: random access and sequential access. Sequential access means reading the elements one by one, starting
at the first element. Linked lists can only do sequential access. If you want to read the 10th element of a linked list, you have to read the first 9 elements and follow the links to the 10th element. Random access means you can jump directly to the 10th element. You’ll frequently hear me say that arrays are faster at reads. This is because they provide random access. A lot of use cases require random access, so arrays are used a lot. Arrays and lists are used to implement other data structures, too



