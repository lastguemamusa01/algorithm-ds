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


