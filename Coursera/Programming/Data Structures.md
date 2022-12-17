University of California San Diego, HSE University

[Google Drive Link](https://drive.google.com/drive/folders/13218vIV7ei3ZKX2-fEbcOGUk60MVQRMD?usp=sharing)

## Week 1 - Basic Data Structures

### Arrays and Linked Lists

#### Arrays

> *contiguous area of memory consisting of equal-size elements indexed by contiguous integers*

- what's so special?
  - Constant-Time:
    1. to access ( read or write ) to any element,
    2. to add or remove at the end,
    3. to add or remove at an arbitrary location
  - its on arithmetic (using the address of an array)
    - <u>array_addr + element_size x ( *i* - first_index )</u>
      - 1000 + 8 ( *i*- 0 ), *if index is 6, what is the address*

#### Multi-Dimensional Arrays

- How to find the address?
  1. skip the row, we are not using: 
     <u>element_size x ( * row- first_index )</u>
  2. then, skip the elements, we are not using:
     <u>{ *1.* } + ( *col - first_index )</u>
  3. As a result, the formula will be as follow:
     <u>array_addr + elem_size x ((rows - first_index) + (col - first_index ))</u>
- Row-Major and Column-major Indexing![image-20211121210956571](C:\Users\Felix\AppData\Roaming\Typora\typora-user-images\image-20211121210956571.png)

##### Times for Common Operations (Arrays)

| *Arrays*      | Add    | Remove |
| :------------ | ------ | ------ |
| **Beginning** | *O(n)* | *O(n)* |
| **End**       | *O(1)* | *O(1)* |
| **Middle**    | *O(n)* | *O(n)* |

---

#### LinkedList

1. *Singly-Linked Lists:*

   - Constant Time to insert at or remove from the front

   - With Tail and Doubly-Linked,

   - Constant time :

     - to insert at, or

     - Remove from the back

   - O(n) time to find arbitrary element

   - List elements need not be contiguous

2. *Double Linked List:*
   - Constant Time to:
     - Insert between Nodes
     - Remove a node

#### Singly-Linked Lists![image-20211121211613626](C:\Users\Felix\AppData\Roaming\Typora\typora-user-images\image-20211121211613626.png)

Node contains:

1. Key
2. Next Pointer

##### List API

| Operations               | Description          |
| :----------------------- | :------------------- |
| PushFront(*Key*)         | add to front         |
| *Key* TopFront()         | return front item    |
| PopFront()               | remove front item    |
| PushBack(*Key*)          | add to back          |
| *Key* TopBack()          | return back item     |
| PopBack()                | remove back item     |
| Boolean Find(*Key*)      | is key in list?      |
| Boolean Empty()          | empty list?          |
| AddBefore(*Node*, *Key*) | adds key before node |
| AddAfter(*Node*, *Key*)  | adds key after node  |

> You have an empty list, and then do the following operations
>
> - PushBack(a)
> - PushFront(b)
> - PushBack(d)
> - PushFront(c)
> - PopBack()
>
> What is the content of the list now?

##### Times for Some Operations (Arrays)

|   *Singly-Linked List*   | no tail | with tail |
| :----------------------: | :-----: | :-------: |
|    **PushFront**(Key)    |  O(1)   |     -     |
|      **TopFront()**      |  O(1)   |           |
|       **PopFront**       |  O(1)   |     -     |
|    **PushBack**(Key)     |  O(n)   |   O(1)    |
|      **TopBack**()       |  O(n)   |   O(n)    |
|      **PopBack()**       |  O(n)   |     -     |
|      **Find**(Key)       |  O(n)   |     -     |
|      **Erase**(Key)      |  O(n)   |     -     |
|       **Empty()**        |  O(1)   |     -     |
| **AddBefore**(Node, Key) |  O(n)   |     -     |
| **AddAfter**(Node, Key)  |  O(1)   |     -     |

##### Pseudocodes (Single Linked List):

1. **PushFront(*key*)**

   ```pseudocode
   node <- new node
   node.key <- key
   node.next <- head
   head <- node
   if tail = nil:
   	tail <- head
   ```

2. **PopFront()**

   ```pseudocode
   if head = nil :
   	ERROR: empty list
   
   head <- head.next
   if head = nil:
   	tail <- nil
   ```

3. **PushBack(*key*)**

   ```pseudocode
   node <- new node
   node.key <- key
   node.next = nil
   if tail = nil:
   	head <- tail <- node
   else:
   	tail.next <- node
   	tail <- node
   ```

4. **PopBack()**

   ```pseudocode
   if head = nil: ERROR: empty list
   if head = tail:
   	head <- tail <- nil
   else:
   	p <- head
   	while p.next.next ≠ nil:
   		p <- p.next
   	p.next <- nil; tail <- p
   ```

> If we do a PopBack on a list containing the keys (in order) a, b, c, and d, we'll execute the following part of the code:
>
> ```pseudocode
> p <- head
> while p.next.next != nil:
>   p <- p.next
> ```
>
> The loop will start with p pointing to the node containing key a.
> How many times will the body of the while loop be executed?

5. **AddAfter**(*node, key*)

   ```pseudocode
   node2 <- new node
   node2.key <- key
   node2.next = node.next
   node.next = node2
   if tail = node:
   	tail <- node2
   ```

---

#### Doubly-Linked List

![image-20211121221726348](C:\Users\Felix\AppData\Roaming\Typora\typora-user-images\image-20211121221726348.png)

Node contains:

1. Key
2. Next pointer
3. Prev pointer

|   *Doubly-Linked List*   | no tail | with tail |
| :----------------------: | :-----: | :-------: |
|    **PushFront**(Key)    |  O(1)   |     -     |
|      **TopFront()**      |  O(1)   |     -     |
|       **PopFront**       |  O(1)   |     -     |
|    **PushBack**(Key)     |  O(n)   |   O(1)    |
|      **TopBack**()       |  O(1)   |   O(1)    |
|      **PopBack()**       |  O(1)   |     -     |
|      **Find**(Key)       |  O(n)   |     -     |
|      **Erase**(Key)      |  O(n)   |     -     |
|       **Empty()**        |  O(1)   |     -     |
| **AddBefore**(Node, Key) |  O(1)   |     -     |
| **AddAfter**(Node, Key)  |  O(1)   |     -     |

##### Pseudocodes (Doubly Linked List)

1. **PushBack**(Key)

   ```pseudocode
   node <- new node
   node.key <- key; node.next = nil
   if tail = nil:
   	head <- tail <- node
   	node.prev <- nil
   else:
   	tail.next <- node
   	node.prev <- tail
   	tail <- node
   ```

2. **PopBack()**

   ```pseudocode
   if head = nil: ERROR: empty list
   if head = tail:
   	head <- tail <- nil
   else:
   	tail <- tail.prev
   	tail.next <- nil
   ```

3. **AddAfter** (node, key)

   ```pseudocode
   node2 <- new node
   node2.key <- key
   node2.next <- node.next
   node.next <- node2
   if node2.next ≠ nil:
   	node2.next.prev <- node2
   if tail = node:
   	tail <- node2
   ```

4. **AddBefore** (node, key)

   ```pseudocode
   node2 <- new node
   node2.key <- key
   node2.next <- node
   node2.prev <- node.prev
   node.prev <- node2
   if node2.prev ≠ nil:
   	node2.prev.next <- node2
   if head = node:
   	head <- node2
   ```

Slide link [here](https://drive.google.com/file/d/1gMkC11f9v-APttcHBmlloQf34hFJJq1n/view?usp=sharing)

---

### Stacks and Queues

#### Stacks

