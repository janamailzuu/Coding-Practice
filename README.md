# Data Structures

# Table of Content
- [Asymptotic Notation](#asymptotic-notation)
- [Data Structures](#data-structures)
  - [Array](#array)
  - [Linked List](#linked-list)
  - [Stack](#stack)
  - [Queue](#queue)
  - [Hash Table or Hash Map](#hash)
  - [Binary Tree](#binary-tree)
  - [Graph](#graph)
- [Algorithms](#algorithms)
  - [Algorithm Basics](#algorithm-basics)
  - [Search Algorithms](#search-algorithms)
    - [Breadth First Search](#breadth-first-search)
    - [Depth First Search](#depth-first-search)
  - [Sorting Algorithms](#sorting-algorithms)
    - [Selection Sort](#selection-sort)
    - [Insertion Sort](#insertion-sort)
    - [Merge Sort](#merge-sort)
    - [Quick Sort](#quick-sort)
- [Additional Resources](#additional-resources)

# <a id="asymptotic-notation"></a>Asymptotic Notation
### Definition:
Asymptotic Notation is the hardware independent notation used to tell the time and space complexity of an algorithm. Meaning it's a standardized way of measuring how much memory an algorithm uses or how long it runs for given an input.

#### Complexities
The following are the Asymptotic rates of growth from best to worst:
- constant growth - ``O(1)`` Runtime is constant and does not grow with `n`
- logarithmic growth – ``O(log n)`` Runtime grows logarithmically in proportion to `n`
- linear growth – ``O(n)`` Runtime grows directly in proportion to `n`
- superlinear growth – ``O(n log n)`` Runtime grows in proportion _and_ logarithmically to `n`
- polynomial growth – `O(n^c)` Runtime grows quicker than previous all based on `n`
- exponential growth – `O(c^n)` Runtime grows even faster than polynomial growth based on `n`
- factorial growth – `O(n!)` Runtime grows the fastest and becomes quickly unusable for even
small values of `n`

[(source: Soumyadeep Debnath, _Analysis of Algorithms | Big-O analysis_)](https://www.geeksforgeeks.org/analysis-algorithms-big-o-analysis/)

Visualized below; the x-axis representing input size and the y-axis representing complexity:

![#](https://upload.wikimedia.org/wikipedia/commons/thumb/7/7e/Comparison_computational_complexity.svg/400px-Comparison_computational_complexity.svg.png)

![#](https://cooervo.github.io/Algorithms-DataStructures-BigONotation/images/graphs/comparison.svg)

[(source: Wikipedia, _Computational Complexity of Mathematical Operations_)](https://en.wikipedia.org/wiki/Computational_complexity_of_mathematical_operations)

#### Big-O notation
Big-O refers to the upper bound of time or space complexity of an algorithm, meaning it worst case runtime scenario. An easy way to think of it is that runtime could be better than Big-O but it will never be worse.
#### Big-Ω (Big-Omega) notation
Big-Omega refers to the lower bound of time or space complexity of an algorithm, meaning it is the best runtime scenario. Or runtime could worse than Big-Omega, but it will never be better.
#### Big-θ (Big-Theta) notation
Big-Theta refers to the tight bound of time or space complexity of an algorithm. Another way to think of it is the intersection of Big-O and Big-Omega, or more simply runtime is guaranteed to be a given complexity, such as `n log n`.

#### What you need to know
- Big-O and Big-Theta are the most common and helpful notations
- Big-O does _not_ mean Worst Case Scenario, Big-Theta does _not_ mean average case, and Big-Omega does _not_ mean Best Case Scenario. They only connote the algorithm's performance for a particular scenario, and all three can be used for any scenario.
- Worst Case means given an unideal input, Average Case means given a typical input, Best case means a ideal input. Ex. Worst case means given an input the algorithm performs particularly bad, or best case an already sorted array for a sorting algorithm.
- Best Case and Big Omega are generally not helpful since Best Cases are rare in the real world and lower bound might be very different than an upper bound.
- Big-O isn't everything. On paper merge sort is faster than quick sort, but in practice quick sort is superior.

#### BIG O NOTATION AND WORST CASE ANALYSIS:

Big O notation is simply a measure of how well an algorithm scales (or its rate of growth). This way we can describe the performance or complexity of an algorithm. Big O notation focuses on the worst-case scenario.

##### Why focus on worst case performance? At first look it might seem counter-intuitive why not focus on best case or at least in average case performance? I like a lot the answer given in The Algorithms Design Manual by S. Skiena:

Imagine you go to a casino what will happen if you bring n dollars?

- The **best case**, is that you walk out owning the casino, it’s possible but so improbable that you don’t even think about it.

- The **average case**, is a little more tricky to prove as you need domain knowledge in order to identify which is the average case. For example, the average case in our example is that the typical bettor loses ~87% of the money that they bring to the casino, but people who are drunk surely loose even more, what about experienced professional players and what exactly is the average? How did they determined it? Who determined the average case? Are their metrics correct? Average case just makes the task of analyzing an algorithm even more complex.

- The **worst case** is that you lose all your n dollars, this is easy to calculate and very likely to happen.

Now think of this in a context of a program with .search() method which takes linear time to execute:

The worst case is O(n), this is when the key is at the end or never present in the list. Which might happen.

The best case is O(1), this happens if and only if the key is at the beginning of the list. Which becomes even more unlikely as n grows.

https://cooervo.github.io/Algorithms-DataStructures-BigONotation/big-O-notation.html

###### Constant time: O(1)

<code>int example = 1;</code>

###### Linear time: O(n)

        for (int i = 0; i < N; i++) {
              //do something in constant time...
        }

###### Quadratic time: O(n2)

           for (int i=0; i < N; i++) {
              for(int j=0; j< N; j++){
         	      		   //do something in constant time...
          	  }
	          }
            
 Another Sample for Quadratic:
                  //This will have a quadratic time look-up since the function is looking at a every index in the array twice.

            var hasDuplicates = function(array) {
                for (var i = 0; i < array.length; i++) {
                  var item = array[i];
                  if (array.slice(i + 1).indexOf(item) !== -1) {
                    return true;
                  }
                }
                return false;
              }; 
 
 ###### Logarithmic time: O(Log n)
         
         for(int i=0; i < n; i *= 2) {
       	  	//do something in constant time...
    	}	
      
Another sample for Logarithmic
      
      for(int i=n; i >=1 ; i /= 2) {
       	  	//do something in constant time...
    	}	
 
 ###### Linearithmic time: O(n*Log n)
        for(int i= 0; i< n; i++) { // linear loop  O(n) * ...
          		for(int j= 1; j< n; j *= 2){ // ...log (n)
              		  //do something in constant time...
          		}
	        }
	
 
##### Exponential Time

Exponential (base 2) running time means that the calculations performed by an algorithm double every time as the input grows.

Examples of exponential runtime algorithms:

Power Set: all the subsets on a set.\

      powerset('') // =>  ['']
      powerset('a') // => ['', 'a']
      powerset('ab') // => ['', 'a', 'b', 'ab']

Fibonacci:
         
         //This will have an exponential time look-up since the function is looking at a every index an exponential number of times.
           var fibonacci = function(number) {
                if (number <= 1) return number;
                return Fibonacci(number - 2) + Fibonacci(number - 1);
              }; 
##### Factorial Time
Factorial is the multiplication of all positive integer numbers less than itself. For instance:

      getPermutations('a') // => [ 'a']
      getPermutations('ab') // =>  [ 'ab', 'ba']
      getPermutations('abc') // => [ 'abc', 'acb', 'bac', 'bca', 'cab', 'cba' ]
      
https://adrianmejia.com/most-popular-algorithms-time-complexity-every-programmer-should-know-free-online-tutorial-course/
               
 ##### Exponential
 
 An exponential algorithm often also iterates through all subsets of the input elements. It is denoted O(2_n_) and is often seen in brute-force algorithms. It is similar to factorial time except in its rate of growth, which as you may not be surprised to hear, is exponential. The larger the data set, the more steep the curve becomes.
 
 ##### Factorial
 
 An algorithm with time complexity O(n!) often iterates through all permutations of the input elements. One common example is a brute-force search seen in the travelling salesman problem. It tries to find the least costly path between a number of points by enumerating all possible permutations and finding the ones with the lowest cost.
 
 Polynimial Complexity:
 - Constant
 - Linear
 - Logarithmic
 -  Linearthmic
 
Non Polynomial Complexity:
 - Exponential
 - Factorial

https://victoria.dev/blog/a-coffee-break-introduction-to-time-complexity-of-algorithms/


# <a id="data-structures"></a>Data Structures
### <a id="array"></a> Array
#### Definition
- Stores data elements based on an sequential, most commonly 0 based, index.

#### What you need to know
- Optimal for indexing; bad at searching, inserting, and deleting (except at the end).
- **Linear arrays**, or 1D arrays, are the most basic.
  	- Are static in size, meaning that they are declared with a fixed size.
- **Dynamic arrays** are like 1D arrays, but have reserved space for additional elements.
  	- If a dynamic array is full, it copies its contents to a larger array.
- **Multi dimensional arrays** nested arrays that allow for multiple dimensions such as an **array of arrays** providing a 2D 	spacial representation via x, y coordinates.


#### Linear arrays

	int[] array = {1,3,5,2,6,9};
	/*
	 * Index: 0 1 2 3 4 5
	 * Value: 1 3 5 2 6 9
	 */
  
![#](https://introcs.cs.princeton.edu/java/11cheatsheet/images/array.png)

![#](https://introcs.cs.princeton.edu/java/11cheatsheet/images/array-init.png)


#### Two-dimensional arrays

![#](https://introcs.cs.princeton.edu/java/11cheatsheet/images/array2d.png)

![#](https://introcs.cs.princeton.edu/java/11cheatsheet/images/array2d-init.png)

#### Time Complexity
- Indexing:         Linear array: `O(1)`,      Dynamic array: `O(1)`
- Search:           Linear array: `O(n)`,      Dynamic array: `O(n)`
- Optimized Search: Linear array: `O(log n)`,  Dynamic array: `O(log n)`
- Insertion:        Linear array: n/a,         Dynamic array: `O(n)`

### <a id="linked-list"></a>Linked List

![#](http://upload.wikimedia.org/wikipedia/commons/1/1b/C_language_linked_list.png)

#### Definition
- Stores data with **nodes** that point to other nodes.
  - Nodes, at its most basic it has one datum and one reference (another node).
  - A linked list _chains_ nodes together by pointing one node's reference towards another node.

#### What you need to know
- Designed to optimize insertion and deletion, slow at indexing and searching.
- **Doubly linked list** has nodes that also reference the previous node.
- **Circularly linked list** is simple linked list whose **tail**, the last node, references the **head**, the first node.
- **Stack**, commonly implemented with linked lists but can be made from arrays too.
  - Stacks are **last in, first out** (LIFO) data structures.
  - Made with a linked list by having the head be the only place for insertion and removal.
- **Queues**, too can be implemented with a linked list or an array.
  - Queues are a **first in, first out** (FIFO) data structure.
  - Made with a doubly linked list that only removes from head and adds to tail.

		// Attributes
		 public class Node {
		      public int value;
		      public Node next;
		      public Node(int value, Node next) {
			  this.value = value;
			  this.next = next;
		      }
		  }
		  // Methods
		  public interface MyList {
		      public int get(int index);
	      
		      public void update(int index, int value);

		      public void append(int value);

		      public String toString();
		  }
![#](https://www.studytonight.com/data-structures/images/doubly-linked-list-1.png)
	  
#### Time Complexity
- Indexing:         Linked Lists: `O(n)`
- Search:           Linked Lists: `O(n)`
- Optimized Search: Linked Lists: `O(n)`
- Insertion:        Linked Lists: `O(1)`

		Array		List
Access		O(1)		O(n)
Update		O(1)		O(n)
Append		O(1)/O(n)	O(1)
Traversal	O(n)		O(n)

### <a id="stack"></a> Stack
 - Stack is an ordered list of similar data type.
 - Stack is a LIFO(Last in First out) structure or FILO(First in Last out).
 - Stack is said to be in Overflow state when it is completely full and is said to be in Underflow state if it is completely empty.

![#](https://www.studytonight.com/data-structures/images/stack-data-structure.png)

	// Last-in first-out data structure
	public interface MyStack {
	    // Add a value to the stack
	    public void push(int value);

	    // Remove a value from the stack
	    public int pop();

	    // See the value on the "top" of the stack (next to be removed)
	    public int peek();
		}
		
	MyStack a = ...; // [ ]
	a.push(1); // [ 1 ]
	a.push(2); // [ 2 1 ]
	a.peek(); // returns 2
	a.push(3); // [ 3 2 1 ]
	a.pop(); // [ 2 1 ], returns 3
	a.push(4); // [ 4 2 1 ]
	a.peek(); // returns 4
	
**Stacks: Standard Library**
	
	Stack<Integer> a = new Stack<Integer>();
	    a.push(1);
	    a.push(2);
	    System.out.println(a.pop()); // 2
	    a.push(3);
	    System.out.println(a); // [1, 3]

#### Application of Stack
  - The simplest application of a stack is to reverse a word. You push a given word to stack - letter by letter - and then pop letters from the stack.
  - Parsing
  - Expression Conversion(Infix to Postfix, Postfix to Prefix etc)

#### Time Complexity
   - Push Operation : O(1)
   - Pop Operation : O(1)
   - Top Operation : O(1)
   - Search Operation : O(n)
### <a id="queue"></a> Queue
	- FIFO data structure
	- in which the first element is inserted from one end called the REAR(also called tail), and the removal of existing element takes place from the other end called as FRONT(also called head).
	
![#](https://www.studytonight.com/data-structures/images/introduction-to-queue.png)

		// First-in first-out data structure
	public interface MyQueue {
	    // Add a value to the back of the queue
	    public void enqueue(int value);

	    // Remove a value from front of the queue
	    public int dequeue();

	    // See the value on the "front" of the queue (next to be removed)
	    public int peek();
	}
	MyStack a = ...; // [ ]
	a.enqueue(1); // [ 1 ]
	a.enqueue(2); // [ 1 2 ]
	a.peek(); // returns 1
	a.enqueue(3); // [ 1 2 3 ]
	a.dequeue(); // [ 2 3 ], returns 1
	a.enqueue(4); // [ 2 3 4 ]
	a.peek(); // returns 2
	
**Queues: Standard Library**

	  import java.util.Queue;
	  import java.util.ArrayDeque;
	  Queue<String> stack = new ArrayDeque<String>();

#### Time Complexity

		Array		List
Enqueue		O(1)/O(n)	O(1)
Dequeue		O(1)		O(1)
Peek		O(1)		O(1)


### <a id="hash"></a> Hash Table or Hash Map
#### Definition
- Stores data with key value pairs.
- **Hash functions** accept a key and return an output unique only to that specific key.
  - This is known as **hashing**, which is the concept that an input and an output have a one-to-one correspondence to map information.
  - Hash functions return a unique address in memory for that data.

#### What you need to know
- Designed to optimize searching, insertion, and deletion.
- **Hash collisions** are when a hash function returns the same output for two distinct inputs.
  - All hash functions have this problem.
  - This is often accommodated for by having the hash tables be very large.
- Hashes are important for associative arrays and database indexing.

**Hash Maps: Standard library**

	import java.util.HashSet;
	import java.util.HashMap;

	// ...

	HashSet<String> set = new HashSet<String>();
	set.add("dog");
	set.add("cat");
	set.add("fish");
	System.out.println(set.contains("dog")); // true
	System.out.println(set.contains("horse")); // false

	HashMap<String, String> map = new HashMap<String, String>();
	map.put("Jenny", "867-5309");
	System.out.println(map.get("Jenny")); // 867-5309

#### Time Complexity
- Indexing:         Hash Tables: `O(1)`
- Search:           Hash Tables: `O(1)`
- Insertion:        Hash Tables: `O(1)`

### <a id = "binary-tree"></a> Binary Tree

![#](http://upload.wikimedia.org/wikipedia/commons/f/f7/Binary_tree.svg)

	public class Node {
	    public int value;
	    public Node left;
	    public Node right;
	    public Node(int value, Node left, Node right) {
		this.value = value;
		this.left = left;
		this.right = right;
	    }
	    public Node(int value) {
		this(value, null, null);
	    }
	}
Fast Vocabulary

Root – The top node in a tree.
Parent – The converse notion of child.
Siblings – Nodes with the same parent.
Descendant – a node reachable by repeated proceeding from parent to child.
Ancestor – a node reachable by repeated proceeding from child to parent.
Leaf – a node with no children.
Edge – connection between one node to another.
Path – a sequence of nodes and edges connecting a node with a descendant.
Level – The level of a node is defined by 1 + the number of connections between the node and the root.
Height – The height of a node is the number of edges on the longest downward path between the root and a leaf.

#### Trees: Binary Search Tree
Binary Search Tree: every value in the left subtree of a node with a value is less than that value; every value in the right subtree of a node with a value is greater than that value.
![#](http://upload.wikimedia.org/wikipedia/commons/d/da/Binary_search_tree.svg)

This gives us O(log(n)) retrieval (in the average but not worst case; more on that later).

Worst Case: Unbalanced Tree
![#](http://epaperpress.com/sortsearch/images/fig33.gif)

### <a id = "graph"></a> Graph
A Graph is a non-linear data structure consisting of nodes and edges. The nodes are sometimes also referred to as vertices and the edges are lines or arcs that connect any two nodes in the graph. 

![#](https://www.geeksforgeeks.org/wp-content/uploads/undirectedgraph.png)


In the above Graph, the set of vertices V = {0,1,2,3,4} and 
	            the set of edges E = {01, 12, 23, 34, 04, 14, 13}.


#### Common Graph Representation
1. Adjacency matrix
2. Adjacency List
3. Edge List

##### Adjacency Matrix
![#](https://media.geeksforgeeks.org/wp-content/uploads/adjacencymatrix.png)

##### Adjacency List
![#](https://media.geeksforgeeks.org/wp-content/uploads/listadjacency.png)

##### Edge List 

E = [[0,1],[0,4],[1,2],[1,3],[1,4],[3,4],[2,3]]


# <a id="additional-resources"></a>Additional Resources

- https://github.com/lichenma/LeetCode-CheatSheet/blob/master/README.md
- https://victoria.dev/blog/a-coffee-break-introduction-to-time-complexity-of-algorithms/
- https://www.studytonight.com/data-structures/
