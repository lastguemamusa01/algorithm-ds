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


### Selection sort

Suppose you have a bunch of music on your computer. For each artist, you have a play count.

You want to sort this list from most to least played, so that you can rank your favorite artists. How can you do it?

One way is to go through the list and find the most-played artist. Add that artist to a new list. repeat and repeat until the list is sorted.

![image](https://user-images.githubusercontent.com/25869911/150656573-03ccccf0-6c9c-4471-8b8e-9cfb8ef609fc.png)


This takes O(n × n) time or O(n^2) time.

Maybe you’re wondering: as you go through the operations, the number of elements you have to check keeps decreasing. Eventually, you’re down to having to check just one element. So how can the run time still be O(n^2)? That’s a good question, and the answer has to do with constants in Big O notation. I’ll get into this more in chapter 4, but here’s the gist.

You’re right that you don’t have to check a list of n elements each time. You check n elements, then n – 1, n - 2 ... 2, 1. On average, you check a list that has 1/2 × n elements. The runtime is O(n × 1/2 × n). But constants like 1/2 are ignored in Big O notation

Selection sort is a neat algorithm, but it’s not very fast. Quicksort is a faster sorting algorithm that only takes O(n log n) time

* Your computer’s memory is like a giant set of drawers.
* When you want to store multiple elements, use an array or a list.
* With an array, all your elements are stored right next to each other.
* With a list, elements are strewn all over, and one element stores the address of the next one.
* Arrays allow fast reads.
* Linked lists allow fast inserts and deletes.
* All elements in the array should be the same type (all ints, all doubles, and so on).

## 3 recursion

Recursion is a coding technique used in many algorithms. 
You learn how to break a problem down into a base case and a recursive case. The divide-and- conquer strategy (chapter 4) uses this simple concept to solve hard problems.


Pseudocode is a high-level description of the problem you’re trying to solve, in code. It’s written like code, but it’s meant to be closer to human speech.

### Recursion


The second way uses recursion. Recursion is where a function calls itself.

Recursion is used when it makes the solution clearer.

There’s no performance benefit to using recursion; in fact, loops are sometimes better for performance. I like this quote by Leigh Caldwell on Stack Overflow: “Loops may achieve a performance gain for your program. Recursion may achieve a performance gain for your programmer. Choose which is more important in your situation!”

### Base case and recursive case

Because a recursive function calls itself, it’s easy to write a
function incorrectly that ends up in an infinite loop.

When you write a recursive function, you have to tell it when to stop recursing. That’s why every recursive function has two parts: the base case, and the recursive case. The recursive case is when the function calls itself. The base case is when the function doesn’t call itself again ... so it doesn’t go into an infinite loop.

### The stack

This section covers the call stack. It’s an important concept in programming. The call stack is an important concept in general programming, and it’s also important to understand when using recursion.

Te stack of sticky notes is much simpler. When you insert an item, it gets added to the top of the list. When you read an item,
you only read the topmost item, and it’s taken off the list. So your todo list has only two actions: push (insert) and pop (remove and read).

![image](https://user-images.githubusercontent.com/25869911/150658199-20e771de-28c0-43f0-a055-8fc64a3be87f.png)


This data structure is called a stack. The stack is a simple data structure.

### The call stack

Your computer uses a stack internally called the call stack. 

def greet(name):
print “hello, “ + name + “!” greet2(name)
print “getting ready to say bye...” bye()

def greet2(name):
print “how are you, “ + name + “?”

def bye():
print “ok bye!”

stack : 

call greet(name) -> greet 

call greet2(name) -> greet2
                     greet
                     
print greet2 and return to greet (pop up the greet 2) -> greet

call bye() -> bye
              greet
print bye() and return to gree(pop up bye) -> greet

### The call stack with recursion

the call stack too! Let’s look at this in action with the factorial function. factorial(5) is written as 5!, and it’s defined like this: 5! = 5 * 4 * 3 * 2 * 1

def fact(x): if x == 1: return 1
else:
return x * fact(x-1)

fact(3)

![image](https://user-images.githubusercontent.com/25869911/150658468-00c51cf8-6dfd-4b4f-a387-606abab81020.png)

![image](https://user-images.githubusercontent.com/25869911/150658471-9d900cd4-72fb-479c-ae60-761d9408aec3.png)

The stack plays a big part in recursion.

Using the stack is convenient because you don’t have to keep track of a pile of boxes yourself—the stack does it for you.

Using the stack is convenient, but there’s a cost: saving all that info can take up a lot of memory. Each of those function calls takes up some memory, and when your stack is too tall, that means your computer is saving information for many function calls. At that point, you have two options:
• You can rewrite your code to use a loop instead.
• You can use something called tail recursion. That’s an advanced recursion topic that is out of the scope of this book. It’s also only supported by some languages, not all.

* Recursion is when a function calls itself.
* Every recursive function has two cases: the base case and the recursive case.
* A stack has two operations: push and pop.
* All function calls go onto the call stack.
* The call stack can get very large, which takes up a lot of memory.

## 4 - quicksort

You learn about divide-and-conquer. Sometimes you’ll come across a problem that can’t be solved by any algorithm you’ve learned. When a good algorithmist comes across such a problem, they don’t just give up. They have a toolbox full of techniques they use on the problem, trying to come up with a solution. Divide-and-conquer is the first general technique you learn

You learn about quicksort, an elegant sorting algorithm that’s often used in practice. Quicksort uses divide-and-conquer.

We’ll explore divide and conquer (D&C), a well-known recursive technique for solving problems.

When you get a new problem, you don’t have to be stumped. Instead, you can ask, “Can I solve this if I use divide and conquer?”

### Divide & conquer

1. Figure out the base case. This should be the simplest possible case.
2. Divide or decrease your problem until it becomes the base case.

Euclid’s algorithm

To recap, here’s how D&C works:
1. Figure out a simple case as the base case.
2. Figure out how to reduce your problem and get to the base case.

When you’re writing a recursive function involving an array, the base case is often an empty array or an array with one element. If you’re stuck, try that first.

Sneak peak at functional programming

Why would I do this recursively if I can do it easily with a loop?” you may be thinking. Well, this is a sneak peek into functional programming! Functional programming languages like Haskell don’t have loops, so you have to use recursion to write functions like this. If you have a good understanding of recursion, functional languages will be easier to learn

Haskell makes heavy use of recursion, it includes all kinds of niceties like this to make recursion easy. If you like recursion, or you’re interested in learning a new language, check out Haskell.

sum [] = 0 Base case
sum (x:xs) = x + (sum xs) Recursive case

### Quicksort

Quicksort is a sorting algorithm. It’s much faster than selection sort and is frequently used in real life.

For example, the C standard library has a function called qsort, which is its implementation of quicksort. Quicksort also uses D&C.

no need to sort when the array is empty or there is one element only.

Empty arrays and arrays with just one element will be the base case. You can just return those arrays as is—there’s nothing to sort:

def quicksort(array): if len(array) < 2:
  return array

Let’s look at bigger arrays. An array with two elements is pretty easy to sort, too.
R = check if first element is smaller than the second. if it is not, swap them

3 elements 

Remember, you’re using D&C. So you want to break down this array until you’re at the base case. Here’s how quicksort works. First, pick an element from the array. This element is called the pivot

We’ll talk about how to pick a good pivot later. For now, let’s say the first item in the array is the pivot.

array:
33 -> 15 -> 10

![image](https://user-images.githubusercontent.com/25869911/150658927-f19a8a27-bfb3-435d-b205-2741ffc19f82.png)

![image](https://user-images.githubusercontent.com/25869911/150658932-62320ebb-12ca-4ab8-8ce4-456179491966.png)


Inductive proofs

You just got a sneak peak into inductive proofs! Inductive proofs are one way to prove that your algorithm works. Each inductive proof has two steps: the base case and the inductive case. Sound familiar? For example, suppose I want to prove that I can climb to the top of a ladder. In the inductive case, if my legs are on a rung, I can put my legs on the next rung. So if I’m on rung 2, I can climb to rung 3. That’s the inductive case. For the base case, I’ll say that my legs are on rung 1. Therefore, I can climb the entire ladder, going up one rung at a time.

You use similar reasoning for quicksort. In the base case, I showed that the algorithm works for the base case: arrays of size 0 and 1. In the inductive case, I showed that if quicksort works for an array of size 1, it will work for an array of size 2. And if it works for arrays of size 2, it will work for arrays of size 3, and so on. Then I can say that quicksort will work for all arrays of any size. 


### Big O notation revisited

Quicksort is unique because its speed depends on the pivot you choose.

![image](https://user-images.githubusercontent.com/25869911/150659018-e86b8b64-f2c0-44c3-bed0-6e938a0516ab.png)

There’s another sorting algorithm called merge sort, which is
O(n log n). Much faster! Quicksort is a tricky case. In the worst case, quicksort takes O(n2) time.

It’s as slow as selection sort! But that’s the worst case. In the average case, quicksort takes O(n log n) time. So you might be wondering:
* What do worst case and average case mean here?
* If quicksort is O(n log n) on average, but merge sort is O(n log n) always, why not use merge sort? Isn’t it faster?

### Merge sort vs. quicksort


![image](https://user-images.githubusercontent.com/25869911/150659080-507c3bb1-b332-47f7-970d-0d64173ccf36.png)

### Average Case vs Worst case

The performance of quicksort heavily depends on the pivot you choose. Suppose you always choose the first element as the pivot. And you
call quicksort with an array that is already sorted. Quicksort doesn’t check to see whether the input array is already sorted. So it will still try to sort it.

![image](https://user-images.githubusercontent.com/25869911/150659167-cf31fbd1-7a9f-4ba4-9e73-9624a760f375.png)


![image](https://user-images.githubusercontent.com/25869911/150659171-36a76630-f1c2-4b41-97c6-f5a506f3dddf.png)


* D&C works by breaking a problem down into smaller and smaller pieces. If you’re using D&C on a list, the base case is probably an empty array or an array with one element.
* If you’re implementing quicksort, choose a random element as the pivot. The average runtime of quicksort is O(n log n)!
* The constant in Big O notation can matter sometimes. That’s why quicksort is faster than merge sort.
* The constant almost never matters for simple search versus binary search, because O(log n) is so much faster than O(n) when your list gets big.


## 5 - hash tables

When a customer buys product, you have to look up the price in a book. If the book is unalphabetized, it can take you a long time to look through every single line for apple. You’d be doing simple search from chapter 1, where you have to look at every line. Do you remember how long that would take? O(n) time. If the book is alphabetized, you could run binary search to find the price of an apple. That would only take O(log n) time.

But as a cashier, looking things up in a book is a pain, even if the book is sorted. You can feel the customer steaming up as you search for items in the book. What you really need is a buddy who has all the names and prices memorized. Then you don’t need to look up anything: you ask her, and she tells you the answer instantly.

Your buddy Maggie can give you the price in O(1) time for any item, no matter how big the book is. She’s even faster than binary search.

### Hash Functions

![image](https://user-images.githubusercontent.com/25869911/150659364-45371d02-e54f-43fd-9112-7febef7135ff.png)

![image](https://user-images.githubusercontent.com/25869911/150659372-b7231c47-3411-4195-887b-fa71895607e7.png)


The hash function tells you exactly where the price is stored, so you don’t have to search at all! This works because

* The hash function consistently maps a name to the same index. Every time you put in “avocado”, you’ll get the same number back. So you can use it the first time to find where to store the price of an avocado, and then you can use it to find where you stored that price.
* The hash function maps different strings to different indexes. “Avocado” maps to index 4. “Milk” maps to index 0. Everything maps to a different slot in the array where you can store its price.
* The hash function knows how big your array is and only returns valid indexes. So if your array is 5 items, the hash function doesn’t return 100 ... that wouldn’t be a valid index in the array.

Put a hash function and an array together, and you get a data structure called a hash table. A hash table is the first data structure you’ll learn that has some extra logic behind it. Arrays and lists map straight to memory, but hash tables are smarter. They use a hash function to intelligently figure out where to store elements.

Hash tables are probably the most useful complex data structure you’ll learn. They’re also known as hash maps, maps, dictionaries, and associative arrays.

A hash table has keys and values. In the book hash, the names of produce are the keys, and their prices are the values. A hash table maps keys to values.

### Use cases

Hash tables are used everywhere. This section will show you a few use cases.

#### Using hash tables for lookups

Your phone has a handy phonebook built in.

Suppose you want to build a phone book like this. You’re mapping people’s names to phone numbers. Your phone book needs to have this functionality:

* Add a person’s name and the phone number associated with that person.
* Enter a person’s name, and get the phone number associated with that name.
* 
This is a perfect use case for hash tables! Hash tables are great when you want to
* Create a mapping from one thing to another thing
* Look something up


Wow, mapping a web address to an IP address? Sounds like a perfect use case for hash tables! This process is called DNS resolution.

google.com -> 74.125.239.133

#### Preventing duplicate entries

#### Using hash tables as a cache

One final use case: caching. If you work on a website, you may have heard of caching before as a good thing to do.

Suppose you have a niece who keeps asking you about planets. “How far is Mars from Earth?” “How far is the Moon?” “How far is Jupiter?” Each time, you have to do a Google search and give her an answer. It takes a couple of minutes. Now, suppose she always asked, “How far is the Moon?” Pretty soon, you’d memorize that the Moon is 238,900 miles away. You wouldn’t have to look it up on Google ... you’d just remember and answer. This is how caching works: websites remember the data instead of recalculating it.

This is called caching. It has two advantages:

* You get the web page a lot faster, just like when you memorized the distance from Earth to the Moon. The next time your niece asks you, you won’t have to Google it. You can answer instantly.
* Facebook has to do less work.

Caching is a common way to make things faster. All big websites use caching. And that data is cached in a hash!

![image](https://user-images.githubusercontent.com/25869911/150659682-da858927-2a03-472f-b678-bd612866721b.png)


hashes are good for
* Modeling relationships from one thing to another thing
* Filtering out duplicates
* Caching/memorizing data instead of making your server do work


### Collisions

Like I said earlier, most languages have hash tables. You don’t need to know how to write your own. So, I won’t talk about the internals of hash tables too much. But you still care about performance! To understand the performance of hash tables, you first need to understand what collisions are.

First, I’ve been telling you a white lie. I told you that a hash function always maps different keys to different slots in the array.


In reality, it’s almost impossible to write a hash function that does this.

And your hash function is really simple: it assigns a spot in the array alphabetically.

![image](https://user-images.githubusercontent.com/25869911/150659785-d6f50703-c00a-4c7d-9417-2fbafe2100c2.png)


### Performance

![image](https://user-images.githubusercontent.com/25869911/150659855-fa967f79-7dec-49dc-ac19-e9cb4dfdad63.png)


### Load factor

This hash table has a load factor of 1. What if your hash table has only 50 slots? Then it has a load factor of 2. There’s no way each item will get its own slot, because there aren’t enough slots! Having a load factor greater than 1 means you have more items than slots in your array. Once the load factor starts to grow, you need to add more slots to your hash table. This is called resizing

for the load factor = 3/4.  -> 4 slots and 3 occupied slots

You need to resize this hash table. First you create a new array that’s bigger. The rule of thumb is to make an array that is twice the size.

Now you need to re-insert all of those items into this new hash table
using the hash function

This new table has a load factor of 3/8. Much better! With a lower load factor, you’ll have fewer collisions, and your table will perform better. A good rule of thumb is, resize when your load factor is greater than 0.7.

You might be thinking, “This resizing business takes a lot of time!” And you’re right. Resizing is expensive, and you don’t want to resize too often. But averaged out, hash tables take O(1) even with resizing.

### A good hash function

A good hash function distributes values in the array evenly. A bad hash function groups values together and produces a lot of collisions.

good hash funciton is SHA function

Hash tables are a powerful data structure because they’re so fast and they let you model data in a different way. You might soon find that you’re using them all the time:

* You can make a hash table by combining a hash function
with an array.
* Collisions are bad. You need a hash function that minimizes collisions.
* Hash tables have really fast search, insert, and delete.
* Hash tables are good for modeling relationships from one item to another item.
* Once your load factor is greater than .07, it’s time to resize your hash table.
* Hash tables are used for caching data (for example, with a web server).
* Hash tables are great for catching duplicates.

## 6 - breadth-first search 

* model a network using a new, abstract data structure: graphs.
* You learn breadth-first search, an algorithm you can run on graphs to answer questions like, “What’s the shortest path to go to X?”'
* directed versus undirected graphs.
* topological sort, a different kind of sorting algorithm that exposes dependencies between nodes.


I’ll talk about what graphs are (they don’t involve an X or Y axis). Then I’ll show you your first graph algorithm. It’s called breadth-first search (BFS).

Breadth-first search allows you to find the shortest distance between two things. But shortest distance can mean a lot of things! You can use breadth-first search to

* Write a checkers AI that calculates the fewest moves to victory
* Write a spell checker (fewest edits from your misspelling to a real word—for example, READED -> READER is one edit)
* Find the doctor closest to you in your network

Graph algorithms are some of the most useful algorithms I know. Make sure you read the next few chapters carefully—these are algorithms you’ll be able to apply again and again.


### Introduction to graphs


![image](https://user-images.githubusercontent.com/25869911/151288811-c896b7b9-e945-4a99-85ed-d536cdae9647.png)

![image](https://user-images.githubusercontent.com/25869911/151288825-199d6523-3f98-42a3-a4b0-d87171687a53.png)


### What is a graph?

![image](https://user-images.githubusercontent.com/25869911/151288844-5a1fc0f9-05a1-48e5-b65e-2d8c10bf7356.png)

### Breadth-first search

Breadth- first search is a different kind of search algorithm: one that runs on graphs. It can help answer two types of questions:

* Question type 1: Is there a path from node A to node B?
* Question type 2: What is the shortest path from node A to node B?

![image](https://user-images.githubusercontent.com/25869911/151289364-6b2fc9d5-296f-4941-9235-10434a92f3d6.png)

![image](https://user-images.githubusercontent.com/25869911/151289387-3de524ac-0329-4827-992c-8b6eec6ae02d.png)

### Finding the shortest path

You’d prefer a first-degree connection to a second-degree connection, and a second-degree connection to a third-degree connection, and so on. So you shouldn’t search any second-degree connections before you make sure you don’t have a first-degree connection who is a mango seller. Well, breadth-first search already does this! The way breadth-first search works, the search radiates out from the starting point. So you’ll check first-degree connections before second-degree connections.

![image](https://user-images.githubusercontent.com/25869911/151289572-ed73644b-276a-40ff-82a4-b0dd825dd7e6.png)


### Queues

A queue works exactly like it does in real life. Suppose you and your friend are queueing up at the bus stop. If you’re before him in the queue, you get on the bus first. A queue works the same way. Queues are similar to stacks. You can’t access random elements in the queue. Instead, there are two only operations, enqueue and dequeue.

![image](https://user-images.githubusercontent.com/25869911/151289746-f6ff8818-31ec-4e06-84ae-d487b36c8567.png)

### Implementing the graph

![image](https://user-images.githubusercontent.com/25869911/151290400-34b67788-5795-4791-b670-77da4e8ad1f4.png)

### Implementing the algorithm

![image](https://user-images.githubusercontent.com/25869911/151290413-485b8bff-b561-4711-9b1c-c76a6ff3d057.png)

![image](https://user-images.githubusercontent.com/25869911/151290682-e36d2eef-d61b-483a-9382-8a1943697081.png)

### Running time

If you search your entire network for a mango seller, that means you’ll follow each edge (remember, an edge is the arrow or connection from one person to another). So the running time is at least O(number of edges).

You also keep a queue of every person to search. Adding one person to the queue takes constant time: O(1). Doing this for every person will take O(number of people) total. Breadth-first search takes O(number of people + number of edges), and it’s more commonly written as O(V+E) (V for number of vertices, E for number of edges).

You could say that this list is sorted, in a way. If task A depends on task B, task A shows up later in the list. This is called a topological sort, and it’s a way to make an ordered list out of a graph. Suppose you’re planning a wedding and have a large graph full of tasks to do—and you’re not sure where to start. You could topologically sort the graph and get a list of tasks to do, in order.

![image](https://user-images.githubusercontent.com/25869911/151291369-88c9a523-8b28-4275-a322-f0266fa172f9.png)

* Breadth-first search tells you if there’s a path from A to B.
* If there’s a path, breadth-first search will find the shortest path.
* If you have a problem like “find the shortest X,” try modeling your problem as a graph, and use breadth-first search to solve.
* A directed graph has arrows, and the relationship follows the direction of the arrow (rama -> adit means “rama owes adit money”).
* Undirected graphs don’t have arrows, and the relationship goes both ways (ross - rachel means “ross dated rachel and rachel dated ross”).
* Queues are FIFO (First In, First Out).
* Stacks are LIFO (Last In, First Out).
* You need to check people in the order they were added to the search list, so the search list needs to be a queue. Otherwise, you won’t get the shortest path.
* Once you check someone, make sure you don’t check them again. Otherwise, you might end up in an infinite loop.


## 7 - Dijkstra's algorithm

weighted graphs: a way to assign more or less weight to some edges.
You learn Dijkstra’s algorithm, which lets you answer “What’s the shortest path to X?” for weighted graphs.
You learn about cycles in graphs, where Dijkstra’s algorithm doesn’t work.

### Working with Dijkstra’s algorithm

![image](https://user-images.githubusercontent.com/25869911/151291921-6050e588-3887-466a-a7bc-29a74f0ce0ed.png)

![image](https://user-images.githubusercontent.com/25869911/151292785-279e3cfc-89e2-415e-bed4-df1ef770000b.png)

### Terminology

![image](https://user-images.githubusercontent.com/25869911/151293196-5779711e-2c03-487d-a417-bdc6e5be467e.png)

### Trading for a piano

![image](https://user-images.githubusercontent.com/25869911/151294334-5fafa56b-dbf5-40c3-a9cf-1021c75fa1b6.png)

![image](https://user-images.githubusercontent.com/25869911/151294349-deb7786c-a7e4-4d56-aa0d-d845ce2b962b.png)

![image](https://user-images.githubusercontent.com/25869911/151294370-0945595c-9b5a-4e15-9c99-bff1f8c12b2a.png)

### Negative-weight edges

![image](https://user-images.githubusercontent.com/25869911/151294912-166db580-4973-4104-92f2-99eed0b020f7.png)

![image](https://user-images.githubusercontent.com/25869911/151294920-d82585d0-7036-48a3-8d22-641b2770b0f0.png)

### Implementation

![image](https://user-images.githubusercontent.com/25869911/151296308-72c9fcfa-5024-4bfe-91f2-6d1e2b7b8aaf.png)

![image](https://user-images.githubusercontent.com/25869911/151296323-77295cd5-2051-4c31-93fb-10252fc80237.png)

![image](https://user-images.githubusercontent.com/25869911/151296346-2aef0886-5c5f-4699-ad42-dc83cc04c134.png)

![image](https://user-images.githubusercontent.com/25869911/151296363-7c3118d3-4f5a-41b6-b1eb-5d4a7a3613ba.png)

![image](https://user-images.githubusercontent.com/25869911/151296382-bfefda57-2a00-4762-9c96-cc026fc0ce47.png)


* Breadth-first search is used to calculate the shortest path for an unweighted graph.
* Dijkstra’s algorithm is used to calculate the shortest path for a weighted graph.
* Dijkstra’s algorithm works when all the weights are positive.
* If you have negative weights, use the Bellman-Ford algorithm.

## 8 - Greedy algorithms

You learn how to tackle the impossible: problems that have no fast algorithmic solution (NP-complete problems).

You learn how to identify such problems when you see them, so you don’t waste time trying to find a fast algorithm for them.

You learn about approximation algorithms, which you can use to find an approximate solution to an NP-complete problem quickly.

You learn about the greedy strategy, a very simple problem-solving strategy.

### The classroom scheduling problem

![image](https://user-images.githubusercontent.com/25869911/151681387-f08b1f9d-f48a-4a85-a946-5502cdbb5883.png)

A greedy algorithm is simple: at each step, pick the optimal move. In this case, each time you pick a class, you pick the class that ends the soonest. In technical terms: at each step you pick the locally optimal solution, and in the end you’re left with the globally optimal solution.

### The knapsack problem

![image](https://user-images.githubusercontent.com/25869911/151681456-82fe1b88-4820-4a68-9a4d-5057019534f0.png)

![image](https://user-images.githubusercontent.com/25869911/151681501-aefad88f-b486-4d68-b7ef-e51863bdf7ce.png)


### The set-covering problem

![image](https://user-images.githubusercontent.com/25869911/151719206-33ca6b6e-425f-40a9-a6c5-2307c8b97879.png)

![image](https://user-images.githubusercontent.com/25869911/151719311-cdeb1fca-6561-44a2-9864-822326dc7827.png)


List every possible subset of stations. This is called the power set. There are 2^n possible subsets.

### approximation algorithms

Greedy algorithms to the rescue! Here’s a greedy algorithm that comes pretty close:

* 1. Pick the station that covers the most states that haven’t been covered yet. It’s OK if the station covers some states that have been covered already.
* 2. Repeat until all the states are covered.

This is called an approximation algorithm. When calculating the exact solution will take too much time, an approximation algorithm will work. Approximation algorithms are judged by

* How fast they are
* How close they are to the optimal solution

Greedy algorithms are a good choice because not only are they simple to come up with, but that simplicity means they usually run fast, too. In this case, the greedy algorithm runs in O(n^2) time, where n is the number of radio stations.

![image](https://user-images.githubusercontent.com/25869911/151719475-addc46eb-7b82-4ed5-b7a8-77ae1b622938.png)

![image](https://user-images.githubusercontent.com/25869911/151719609-becbb6a6-3ff5-42ef-ba8f-dbe3a31d75b1.png)

![image](https://user-images.githubusercontent.com/25869911/151719757-d243fe42-85a6-4583-b158-8f0195a797b9.png)


### NP-complete problems

To solve the set-covering problem, you had to calculate every possible set.

![image](https://user-images.githubusercontent.com/25869911/151719946-5ab080b6-6d83-455f-a286-c45f044ace0f.png)

![image](https://user-images.githubusercontent.com/25869911/151720086-6c789914-8e1a-413c-896d-08e798a59740.png)


This is called the factorial function (remember reading about this in chapter 3?). So 5! = 120. Suppose you have 10 cities. How many possible routes are there? 10! = 3,628,800. You have to calculate over 3 million possible routes for 10 cities. As you can see, the number of possible routes becomes big very fast! This is why it’s impossible to compute the “correct” solution for the traveling-salesperson problem if you have a large number of cities.

The traveling-salesperson problem and the set-covering problem both have something in common: you calculate every possible solution and pick the smallest/shortest one. Both of these problems are NP-complete.

![image](https://user-images.githubusercontent.com/25869911/151720189-5aabd75e-e2bc-486a-a3c5-25b05322c99d.png)

### How do you tell if a problem is NP-complete?

![image](https://user-images.githubusercontent.com/25869911/151720233-6dbd2a90-84d2-42b2-bc80-dab569d8fad6.png)

![image](https://user-images.githubusercontent.com/25869911/151720348-e9a5c842-5197-48c6-9aa2-feba5f1d3c3f.png)


### Recap

* Greedy algorithms optimize locally, hoping to end up with a global optimum.
* NP-complete problems have no known fast solution.
* If you have an NP-complete problem, your best bet is to use an approximation algorithm.
* Greedy algorithms are easy to write and fast to run, so they make good approximation algorithms.

## 9 - dynamic programming

* You learn dynamic programming, a technique to solve a hard problem by breaking it up into subproblems and solving those subproblems first.

### The knapsack problem

You’re a thief with a knapsack that can carry 4 lb of goods.

![image](https://user-images.githubusercontent.com/25869911/151720671-df826129-cdec-4aec-a48d-e2cd0bdfb43b.png)

![image](https://user-images.githubusercontent.com/25869911/151721783-afc69277-f85f-4715-991d-d0117037cf1b.png)

![image](https://user-images.githubusercontent.com/25869911/151721867-bbbaf897-45af-4b77-9751-5145249fccd5.png)

![image](https://user-images.githubusercontent.com/25869911/151721940-6e1dc2a0-f3e8-41b2-9541-de9ec3c5528d.png)

![image](https://user-images.githubusercontent.com/25869911/151722018-2912d940-2937-4118-94e0-93dd2f446518.png)

### Knapsack problem FAQ

![image](https://user-images.githubusercontent.com/25869911/151722073-076971a8-9049-4ee3-8aa9-baa25198d69e.png)

![image](https://user-images.githubusercontent.com/25869911/151722139-40594ace-8235-440e-a983-359f49fe3708.png)

![image](https://user-images.githubusercontent.com/25869911/151722253-8d5c704e-dd63-48e3-90c3-d736da8b6fa4.png)

![image](https://user-images.githubusercontent.com/25869911/151722413-a7bb3adf-2855-4ec9-8816-6bf3713b49db.png)

![image](https://user-images.githubusercontent.com/25869911/151722567-f0daf9bf-e52c-4e80-a494-0f73a9c4946a.png)

Is it possible that the best solution doesn’t fill the knapsack completely?

* Yes. Suppose you could also steal a diamond. This is a big diamond: it weighs 3.5 pounds. It’s worth a million dollars, way more than anything else. You should definitely steal it! But there’s half a pound of space left, and nothing will fit in that space.

### Longest common substring

* Dynamic programming is useful when you’re trying to optimize something given a constraint. In the knapsack problem, you had to maximize the value of the goods you stole, constrained by the size of the knapsack.
* You can use dynamic programming when the problem can be broken into discrete subproblems, and they don’t depend on each other.

![image](https://user-images.githubusercontent.com/25869911/151722742-2b01fbcf-9014-446e-9b0e-334ec2e7b1e3.png)

![image](https://user-images.githubusercontent.com/25869911/151722831-aae798be-3da9-4030-84b1-1dee3fe918aa.png)

![image](https://user-images.githubusercontent.com/25869911/151722996-e6115762-9a38-483f-aa28-736487b3954d.png)

![image](https://user-images.githubusercontent.com/25869911/151723059-e296d89f-4a51-4df2-8d8c-31fc8ffbc7bf.png)


Whew—you did it! This is definitely one of the toughest chapters in the book. So is dynamic programming ever really used? Yes:

* Biologists use the longest common subsequence to find similarities in DNA strands. They can use this to tell how similar two animals or two diseases are. The longest common subsequence is being used to find a cure for multiple sclerosis.
* Have you ever used diff (like git diff)? Diff tells you the differences between two files, and it uses dynamic programming to do so.
* We talked about string similarity. Levenshtein distance measures how similar two strings are, and it uses dynamic programming. Levenshtein distance is used for everything from spell-check to figuring out whether a user is uploading copyrighted data.
* Have you ever used an app that does word wrap, like Microsoft Word? How does it figure out where to wrap so that the line length stays consistent? Dynamic programming!

### Recap

* Dynamic programming is useful when you’re trying to optimize something given a constraint.
* You can use dynamic programming when the problem can be broken into discrete subproblems.
* Every dynamic-programming solution involves a grid.
* The values in the cells are usually what you’re trying to optimize.
* Each cell is a subproblem, so think about how you can divide your problem into subproblems.
* There’s no single formula for calculating a dynamic-programming solution.

## 10 - k-nearest neighbors

* You learn to build a classification system using the k-nearest neighbors algorithm.
* You learn about feature extraction.
* You learn about regression: predicting a number, like the value of a stock tomorrow, or how much a user will enjoy a movie.
* You learn about the use cases and limitations of k-nearest neighbors.

### Classifying oranges vs. grapefruit

Look at this fruit. Is it an orange or a grapefruit? Well, I know that grapefruits are generally bigger and redder.

![image](https://user-images.githubusercontent.com/25869911/151723194-80a0c608-d64a-4cdf-95a4-9a8fedf4b025.png)

![image](https://user-images.githubusercontent.com/25869911/151723294-11f0e837-3c85-48cf-ab73-e68308d6ec40.png)

![image](https://user-images.githubusercontent.com/25869911/151723367-09f37067-3711-4774-b65a-4025f7b565ac.png)

![image](https://user-images.githubusercontent.com/25869911/151723512-9e9594fc-c62e-4abb-854f-0d575ff1b4c9.png)


### Regression

![image](https://user-images.githubusercontent.com/25869911/151723782-be544b03-c37b-4047-a153-fe71e757cd5d.png)

![image](https://user-images.githubusercontent.com/25869911/151723788-3c5f43c4-987d-4ad2-9249-f78acf4195a5.png)

![image](https://user-images.githubusercontent.com/25869911/151723793-dbf66fb2-fdf2-4bef-8cff-3cc757e460ff.png)

### Introduction to machine learning

![image](https://user-images.githubusercontent.com/25869911/151724042-51e46271-e377-440f-9ad8-747468ed7990.png)

![image](https://user-images.githubusercontent.com/25869911/151724050-64ef4bda-6ca8-4c27-849e-45debbbe3b9d.png)


### Recap

I hope this gives you an idea of all the different things you can do with KNN and with machine learning! Machine learning is an interesting field that you can go pretty deep into if you decide to:

# KNN is used for classification and regression and involves looking at the k-nearest neighbors.
# Classification = categorization into a group.
# Regression = predicting a response (like a number).
# Feature extraction means converting an item (like a fruit or a user) into a list of numbers that can be compared.
# Picking good features is an important part of a successful KNN algorithm.


## 11 - where to go next

You get a brief overview of 10 algorithms that weren’t covered in this book, and why they’re useful.

### Trees

![image](https://user-images.githubusercontent.com/25869911/151724319-47b1aaa4-d6ce-49da-ba19-17297f0c6d1b.png)

![image](https://user-images.githubusercontent.com/25869911/151724325-701e4c0f-5dba-42b0-bf1d-d39529e1193d.png)

![image](https://user-images.githubusercontent.com/25869911/151724328-20bd9148-37a2-40ee-8abc-6343c24f8493.png)



### Inverted indexes

![image](https://user-images.githubusercontent.com/25869911/151724419-7fb568ef-3dc6-4c20-be09-5cd2b79705a4.png)


### The Fourier transform

The Fourier transform is one of those rare algorithms: brilliant,
elegant, and with a million use cases. The best analogy for the Fourier transform comes from Better Explained (a great website that explains math simply): given a smoothie, the Fourier transform will tell you the ingredients in the smoothie.1 Or, to put it another way, given a song, the transform can separate it into individual frequencies.

It turns out that this simple idea has a lot of use cases. For example, if you can separate a song into frequencies, you can boost the ones you care about. You could boost the bass and hide the treble. The Fourier transform is great for processing signals. You can also use it to compress music. First you break an audio file down into its ingredient notes. The Fourier transform tells you exactly how much each note contributes
to the overall song. So you can just get rid of the notes that aren’t important. That’s how the MP3 format works!

Music isn’t the only type of digital signal. The JPG format is another compressed format, and it works the same way. People use the Fourier transform to try to predict upcoming earthquakes and analyze DNA.

You can use it to build an app like Shazam, which guesses what song is playing. The Fourier transform has a lot of uses. Chances are high that you’ll run into it!

### Parallel algorithms

The next three topics are about scalability and working with a lot of data. Back in the day, computers kept getting faster and faster. If you wanted to make your algorithm faster, you could wait a few months, and the computers themselves would become faster. But we’re near the end of that period. Instead, laptops and computers ship with multiple cores. To make your algorithms faster, you need to change them to run in parallel across all the cores at once!

Here’s a simple example. The best you can do with a sorting algorithm is roughly O(n log n). It’s well known that you can’t sort an array in O(n) time—unless you use a parallel algorithm! There’s a parallel version of quicksort that will sort an array in O(n) time.

Parallel algorithms are hard to design. And it’s also hard to make sure they work correctly and to figure out what type of speed boost you’ll see. One thing is for sure—the time gains aren’t linear. So if you have two cores in your laptop instead of one, that almost never means your algorithm will magically run twice as fast. There are a couple of reasons for this:

* Overhead of managing the parallelism—Suppose you have to sort an array of 1,000 items. How do you divide this task among the two cores? Do you give each core 500 items to sort and then merge the two sorted arrays into one big sorted array? Merging the two arrays takes time.
* Load balancing—Suppose you have 10 tasks to do, so you give each core 5 tasks. But core A gets all the easy tasks, so it’s done in 10 seconds, whereas core B gets all the hard tasks, so it takes a minute. That means core A was sitting idle for 50 seconds while core B was doing all the work! How do you distribute the work evenly so both cores are working equally hard?

If you’re interested in the theoretical side of performance and scalability, parallel algorithms might be for you!

### MapReduce

There’s a special type of parallel algorithm that is becoming increasingly popular: the distributed algorithm. It’s fine to run a parallel algorithm on your laptop if you need two to four cores, but what if you need hundreds of cores? Then you can write your algorithm to run across multiple machines. The MapReduce algorithm is a popular distributed algorithm. You can use it through the popular open source tool
Apache Hadoop.

### Why are distributed algorithms useful?

Suppose you have a table with billions or trillions of rows, and you want to run a complicated SQL query on it. You can’t run it on MySQL, because it struggles after a few billion rows. Use MapReduce through Hadoop!

Or suppose you have to process a long list of jobs. Each job takes 10 seconds to process, and you need to process 1 million jobs like this. If you do this on one machine, it will take you months! If you could run it across 100 machines, you might be done in a few days.

Distributed algorithms are great when you have a lot of work to do and want to speed up the time required to do it. MapReduce in particular is built up from two simple ideas: the map function and the reduce function.

### the map function

![image](https://user-images.githubusercontent.com/25869911/151724668-f7e1c279-486d-4779-a4bb-e7b9a2c6dbf8.png)

![image](https://user-images.githubusercontent.com/25869911/151724671-9db8ffea-d52f-4488-90c0-4079247be591.png)


In this case, you sum up all the elements in the array: 1 + 2 + 3 + 4 + 5 = 15! I won’t explain reduce in more detail here, because there are plenty of tutorials online.

MapReduce uses these two simple concepts to run queries about data across multiple machines. When you have a large dataset (billions
of rows), MapReduce can give you an answer in minutes where a traditional database might take hours.


### Bloom filters and HyperLogLog

![image](https://user-images.githubusercontent.com/25869911/151725239-ec61c315-6c52-4fd9-b5f7-2dba7547f69c.png)

![image](https://user-images.githubusercontent.com/25869911/151725256-e4c72629-c364-478e-9c1e-8ab0b4b28af7.png)

![image](https://user-images.githubusercontent.com/25869911/151725265-fc40cd46-e01d-4b0c-8804-c833d5013938.png)

### The SHA algorithms

![image](https://user-images.githubusercontent.com/25869911/151725386-1397bcca-b285-4d16-9d2b-16522981987c.png)

![image](https://user-images.githubusercontent.com/25869911/151725391-e2449c7a-da81-408d-9789-89410baca76d.png)

![image](https://user-images.githubusercontent.com/25869911/151725395-9e887929-f737-48d1-8ce9-73866678184a.png)


* Scribd allows users to upload documents or books to share with others. But Scribd doesn’t want users uploading copyrighted content! The site could use Simhash to check whether an upload is similar to a Harry Potter book and, if so, reject it automatically.
Simhash is useful when you want to check for similar items.


### Diffie-Hellman key exchange

![image](https://user-images.githubusercontent.com/25869911/151725472-afff53f2-25a7-480c-8c10-c13a1363c46d.png)


That worked! A simple cipher like this is easy to break. The Germans used a much more complicated cipher in WWII, but it was still cracked. Diffie-Hellman solves both problems:

* Both parties don’t need to know the cipher. So we don’t have to meet and agree to what the cipher should be.
* The encrypted messages are extremely hard to decode.

Diffie-Hellman has two keys: a public key and a private key. The public key is exactly that: public. You can post it on your website, email it
to friends, or do anything you want with it. You don’t have to hide it. When someone wants to send you a message, they encrypt it using
the public key. An encrypted message can only be decrypted using the private key. As long as you’re the only person with the private key, only you will be able to decrypt this message!

The Diffie-Hellman algorithm is still used in practice, along with its successor, RSA. If you’re interested in cryptography, Diffie-Hellman is a good place to start: it’s elegant and not too hard to follow.

### Linear programming

I saved the best for last. Linear programming is one of the coolest things I know.

Linear programming is used to maximize something given some constraints. For example, suppose your company makes two products, shirts and totes. Shirts need 1 meter of fabric and 5 buttons. Totes need 2 meters of fabric and 2 buttons. You have 11 meters of fabric and 20 buttons. You make $2 per shirt and $3 per tote. How many shirts and totes should you make to maximize your profit?

Here you’re trying to maximize profit, and you’re constrained by the amount of materials you have.
Another example: you’re a politician, and you want to maximize the number of votes you get. Your research has shown that it takes an average of an hour of work (marketing, research, and so on) for each vote from a San Franciscan or 1.5 hours/vote from a Chicagoan. You need at least 500 San Franciscans and at least 300 Chicagoans. You have 50 days. It also costs you $2/San Franciscan versus $1/Chicagoan. Your total budget is $1,500. What’s the maximum number of total votes you can get (San Francisco + Chicago)?

Here you’re trying to maximize votes, and you’re constrained by time and money.

You might be thinking, “You’ve talked about a lot of optimization topics in this book. How are they related to linear programming?” All the graph algorithms can be done through linear programming instead. Linear programming is a much more general framework, and graph problems are a subset of that. I hope your mind is blown!

Linear programming uses the Simplex algorithm. It’s a complex algorithm, which is why I didn’t include it in this book. If you’re interested in optimization, look up linear programming!


