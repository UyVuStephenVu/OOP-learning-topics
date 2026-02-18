# Linked List

## I. what is a Linked List?

>A linked list is a collection of nodes, where each node contains the Data (the value you store) and a reference (pointer) to the next node in the list.  
>Instead of being stored in one continuous block of memory (like arrays), nodes are scattered in memory and linked together.

>Visualized: [10 | next] → [20 | next] → [30 | next] → null

> Each [] is a node, and null is the end of an LL.

**Types of linked list:**

* singly linked list
* doubly linked list
* circular linked list

in this week, we focus only on singly linked list.

## II. Why and when Use Linked Lists Over Arrays?

* Arrays

    * ✔ Fast random access
    * ✔ Simple structure
    * ❌ Fixed size (in many languages)
    * ❌ Inserting/removing elements is expensive

* Linked Lists

    * ✔ Dynamic size
    * ✔ Fast insertions/deletions
    * ❌ No random access
    * ❌ Extra memory for pointers

In short, use arrays when you need fast index access, simple iteration, and efficient storage for mostly fixed-size data, and use linked lists when you need frequent insertions or deletions and don’t need random access.

## III. How to write a singly linked list in Typescript.

```ts
//define a Node.
class Node {
  next: Node | null = null;
  data: number;
  constructor(data: number) {
    this.data = data;
  }
}
//define a linked list
class LinkedList {
  head: Node | null = null;
  //add() method adds a new value to the end of the linked list.
  add(data: number) {
    const node = new Node(data);
    if (!this.head) {
      this.head = node;
      return;
    }
    let tail = this.head;
    while (tail.next) {
      tail = tail.next;
    }
    tail.next = node;
  }

  //at() method walks the list node by node until it reaches the requested index.
  at(index: number) {
    if (!this.head) throw new Error("Index out of bounds");
    let counter = 0;
    let node: Node | null = this.head;
    while (node) {
      if (counter === index) {
        return node;
      }
      counter++;
      node = node.next;
    }
    throw new Error("Out of bounds");
  }

  //print() method iterates through the entire list and prints each value.
  print() {
    if (!this.head) {
      return;
    }
    let node: Node | null = this.head;
    while (node) {
      console.log(node.data);
      node = node.next;
    }
  }
}

//Create an empty linked list
const ll = new LinkedList();
```