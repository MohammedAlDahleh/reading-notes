## Things I want to know more about
<h2>Big O</h2>

[Big-O](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-05/resources/big_oh.html)

- Big O(oh) notation is used to describe the efficiency of an algorithm or function.

* we should consider 4 Key Areas for analysis:
1. Input Size
2. Units of Measurement
3. Orders of Growth
4. Best Case, Worst Case, and Average Case
<h2>Linked Lists </h2>
* Terminology:
1. Linked List - A data structure that contains nodes that links/points to the next node in the list.
2. Singly - Singly refers to the number of references the node has. A Singly linked list means that there is only one reference, and the reference points to the Next node in a linked list.
4. Doubly - Doubly refers to there being two (double) references within the node. A Doubly linked list means that there is a reference to both the Next and Previous node.
5. Node - Nodes are the individual items/links that live in a linked list. Each node contains the data for each link.
6. Next - Each node contains a property called Next. This property contains the reference to the next node.
7. Head - The Head is a reference of type Node to the first node in a linked list.
8. Current - The Current is a reference of type Node to the node that is currently being looked at. When traversing, you create a new Current variable at the Head to guarantee you are starting from the beginning of the linked list.

* What does it look like
- This is what a Singly Linked List looks like

[Singly-Linked](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-05/resources/images/LinkedList1.PNG)

* Traversal
- When traversing a linked list, you are not able to use a foreach or for loop. We depend on the Next value in each node to guide us where the next reference is pointing. The best way to approach a traversal is through the use of a while() loop.

* Traversal Example
--- 
ALGORITHM Includes (value)
 // INPUT <-- integer value
 // OUTPUT <-- boolean

  Current <-- Head

  WHILE Current is not NULL
    IF Current.Value is equal to value
      return TRUE

    Current <-- Current.Next

  return FALSE
---

* Adding a Node:

- Adding O(1)
1. We can then instantiate the new node that we are adding. The values passed in as arguments into the Add() method will define what the value of the Node will be. [image](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-05/resources/images/LinkedList2.PNG)

2. newNode.Next by default is set to null. We want to set newNode.Next property to the same location that the Head node is pointing towards. Because Head is just a reference type, we will be assigning it to the same allocation in memory as the node it is pointing too. In this case, it’s Node1. [image](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-05/resources/images/LinkedList3.PNG)

3. At this point in the program we now “technically” have newNode at the beginning of the linked list, but we are not done yet. We now have to re-assign where Head is pointing too. Since Node1 is no longer the first node in the list, we want to re-assign Head to point at newNode. [image](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-05/resources/images/LinkedList4.PNG)

* Add Code:

---
 ALGORITHM Add(newValue)
 // INPUT <-- Value to add
 // OUTPUT <-- No output

  newNode <-- NEW Node
  newNode.Value <-- newValue
  newNode.Next <-- Head
  Head <-- newNode
---


* LinkedList:
[Linked-List-Part1](https://medium.com/basecs/whats-a-linked-list-anyway-part-1-d8b7e6508b9d)
[Linked-List-Part2](https://medium.com/basecs/whats-a-linked-list-anyway-part-2-131d96f71996)
- This is the second installment in a two-part series on Linked Lists. If you haven’t read Part 1 of this series, I recommend checking that out first!

- Linked lists are super simple, but they seem to have this reputation of being fairly complicated. Their reputation, as they say, precedes them.
[Arrays-vs-LinkedList](https://miro.medium.com/max/1400/1*cUehR5S18XSoVLaPNfNzlA.jpeg)

