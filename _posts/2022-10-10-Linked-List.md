# Data Structures: Linked List and Doubly Linked lis 
## A. Linked List
## I. Conceptual
### What is a linked list?

 Linked lists are one of the basic data structures used in computer science. They have many direct applications and serve as the foundation for more complex data structures.
 ![linked list](https://www.educative.io/api/page/6100383094013952/image/download/4542257903435776)

  The list is comprised of a series of nodes as shown in the diagram above. The _head node_ is the node at the beginning of the list. Each node contains _data_ and a _link_ (or pointer) to the next node in the list. The list is terminated when a node’s link is **_null_**. This last node is called the _tail node_.

  You can understand it like a one-way bus, the trip can move through 1 stop (button) and continue to other stops (link or pointer). In this example, the initial departure station is the head node and the final destination station is the tail node.

  Since nodes use association to represent the next node in the chain, the nodes are not required to be located sequentially in memory. These links also allow quick insertion and removal of nodes.

  Common operations on linked list:

  + adding nodes
  + removing nodes
  + finding a node
  + traversing the linked list
  + And some more advanced operations like: swapping nodes, insert nodes in the middle,....

  In the example below, we have added values to the linked list diagram:
  ![linkedlist](https://i2.wp.com/www.rubyguides.com/wp-content/uploads/2017/07/linked-list-with-label.png?ssl=1)

  This linked list contains three nodes. Each node in this list contains an integer as its data. When the sequence is determined, the order is 10, 20 and 30.

  The list ends at a node with data of 30 because the link in that node is absent (or set to null).

### Algorithm complexity of linked list
 
 Where n is the number of linked elements: 
 - Add an element at the end of the list: O(n) because it has to go through all the elements to get the node at the end 
 - Add an element at the beginning of the list: O(1) 
 - Browse over all elements O(n) 
 - Remove 1 element: Best case is the beginning of the linked list O(1) and the rest is O(n).

## II. Ideas
#### _Creation of Linkded list_
As you know nodes are the most basic building blocks of data structures, and a linked list is made up of interconnected nodes. So we will create another linked list class to use the button class we created in the previous post.

#### _Then we create a new node_
+ if the head is nil it means the list is empty, this would imply that the new node is the head
+ if head is not nil then there are element in the list
+ Iterate over the list from the beginning, until next_node is nil, then the current node is the last node of the linked list.

#### _Common operations of linked list_
**Next, we'll define methods for our LinkedList class to allow us to be able to:**
+ insert a new node at the top 
+ print them out in the terminal
+ remove a node
+ find a node

#### _Some more advanced operations such as_:
+ insert node in the middle of linked list 
+ swapping node,...

## III. Implementation
```bash
class Node
  attr_accessor :data, :next_node
  def initialize(data, next_node = nil)
    @data = data
    @next_node = next_node
  end
end

class LinkedList
  def initialize(value)
    @head_node = nil
  end 

  def head_node
    @head_node
  end 
end
```
#insert a new node at the top:
  ```bash
  def insert(value)
    new_node = Node.new(value)
    new_node.next_node = head_node
    @head_node = new_node
  end
```
#remove a value:
```bash
  def remove(value_to_remove)
    current = head_node
    if current.data == value_to_remove
      @head_node = current.next_node
    else
      loop do
        next_node = current.next_node
        if next_node.data == value_to_remove
          current.next_node = next_node.next_node
          break
        else
          current = next_node
        end
      end
    end
  end
```
#find a node:
```bash
  def find_node(value_to_find)
    return if value.nil?

    node = head_node
    prev =nil

    loop do
    break if node.data == value_to_find

    prev = node
    node = node.next_node

    return node, prev
  end
```
#print linked list
```bash
  def print 
    print_list = ""
    current = head_node

    loop do
    print_list += "#{current.data} -> "
    current = current.next_node
    break if current.nil?
  end
```

#some operations are more complicated:

+ swapping node:
```bash
  def swap_nodes(val1, val2)
   #find node1 and previous of node1
    node1, prev1 = find_node(val1)

   #find node2 and previous of node 2
    node2, prev2 = find_node(val2)


    if node1 == node2
      puts "Elements are the same - no swap needed"
      return
    end
     
    if node1 == nil || node2 == nil
      puts "Swap not possible - one or more element is not in the list"
      return
    end
    #update previous pointer
    #check prev1 is nil
    if prev1 == nil 
      head_node = node2
    else
      prev1.next_node = node2
    end
   #check prev2 is nil 
    if prev2 == nil 
      head_node = node1
    else 
      prev2.next_node = node1
    end
    
    #update next pointer
    next_node_of_node1 = node1.next_node
    node1.next_node = node2.next_node
    node2.next_node = next_node_of_node1

  end
```

+ insert middle:
```bash
  def insert_middle(new_value)
    new_node = Node.new(new_value)

    if head_node == nil
      head_node = new_node
    else
      temp = head_node
      middle = head_node
      while temp.next_node != nil && temp.next_node.next_node != nil
        temp = temp.next_node.next_node
        middle = middle.next_node
      end
      new_node.next_node = middle.next_node
      middle.next_node = new_node
    end
  end
```

#### And some other operations, we will update later.

## B. Doubly Linked List
## I. Conceptual
### What is a Doubly Linked List?
![Doubly LinkedList](https://media.geeksforgeeks.org/wp-content/cdn-uploads/gq/2014/03/DLL1.png)

  Like a singly linked list, a doubly linked list consists of a series of nodes. But each node contains data and two links (or pointers) to the next and previous nodes in the list.

  The _head node_ is the node at the top of the list and the _tail node_ is the node at the end of the list. The _previous pointer_ of the _head node_ is set to **_null_** and the _next pointer_ of the _tail node_ is set to **_null_**.

![DLL](https://skilled.dev/images/linked-list-train.jpg)
  Think of the train as a real-life example of a doubly linked list. The train's cockpit is at the top of the list, the last car is at the bottom, and each car in the middle is another node on the list.
  Each wagon has 2 links like the next node and the previous node of a node in the list.

## II. Ideas
  In a doubly linked list, because there are 2 pointers, the operation is more complicated than in a singly linked list. We have to track and set the node's next and previous pointers and update the tail of the list if necessary.

  Because of the addition of the pointer and tail properties, adding and removing the head of a doubly linked list is a bit more complicated than a single linked list. However, the previous pointer and tail property makes it much simpler to remove the tail of the list because we don't have to traverse the entire list to be able to do that.

1. **Add to the head:**
  ![add head](https://media.geeksforgeeks.org/wp-content/cdn-uploads/gq/2014/03/DLL_add_front1.png)
When adding to the head of the doubly linked list, we first need to check if there is a current head to the list. If there isn’t, then the list is empty, and we can simply make our new node both the head and tail of the list and set both pointers to **_null_**. If the list is not empty, then we will:

+ Set the current head’s previous pointer to our new head.
+ Set the new head’s next pointer to the current head.
+ Set the new head’s previous pointer to **_null_**.

2. **Add to the tail:**
![add tail](https://media.geeksforgeeks.org/wp-content/cdn-uploads/gq/2014/03/DLL_add_end1.png)
Similarly, there are two cases when adding a node to the tail of a doubly linked list. If the list is empty, then we make the new node the head and tail of the list and set the pointers to **_null_**. If the list is not empty, then we:

+ Set the current tail’s next pointer to the new tail
+ Set the new tail’s previous pointer to the current tail
+ Set the new tail’s next pointer to **_null_**

3. **Removing the head:**

Removing the head involves updating the pointer at the beginning of the list. We'll set the new head's previous pointer (the element immediately after the current head) to **_null_** and update the list's head property. If the head is also the tail (the list has only one node), then the tail removal will also occur.

4. **Removing the tail:**

Similarly, removing the tail involves updating the pointer at the end of the list. We'll set the new tail's next pointer (the element immediately before the tail) to null and update the list's tail property. If the tail is also the head, the process of removing the head will also occur.

5. **Remove a any value in list:**

It is also possible to remove a node from the middle of the list. Since that node is neither the head nor the tail of the list, there are two pointers that must be updated:

+ We must set the removed node’s preceding node’s next pointer to its following node.
+ We must set the removed node’s following node’s previous pointer to its preceding node.

+ There is no need to change the pointers of the removed node, as updating the pointers of its neighboring nodes will remove it from the list. If no nodes in the list are pointing to it, the node is orphaned.

6. **There are also some other operations such as:**
 
 +

## III. Implementation

**We create a class node to initialize the linked list:**
```bash
class Node
  attr_accessor :next_node, :prev_node

  def initialize(value, next_node=nil, prev_node=nil)
    @value = value
    @next_node = nil 
    @prev_node = nil
  end
   
  def get_value
    return @value
  end
end
```
**Next, we will create a doubly linked List class and perform the main operations (methods) for it:**
```bash
class DoublyLinkedList
  def initialize(value)
    node = Node.new(value)
    @head_node = node 
    @tail_node = node 
  end

  def head_node
    @head_node
  end 
  
  def tail_node
    @tail_node
  end
```

1. **Add to the head:**
```bash
 def add_head(new_value)
    new_head = Node.new(new_value)
    current_head = head_node

    if current_head != nil
      current_head.prev_node = new_head
      new_head.next_node = current_head
    end

    @head_node = new_head
     
    if tail_node == nil
      @tail_node = new_head
    end
  end
```

2. **Add to the tail:**
```bash
  def add_tail(new_value)
    new_tail = Node.new(new_value)
    current_tail = tail_node

    if current_tail != nil
      current_tail.next_node = new_tail
      new_tail.prev_node = current_tail
    end

    @tail_node = new_tail

    if head_node == nil
      @head_node = new_tail
    end
  end
```

3. **Removing the head:**
```bash
 def remove_head_node
     remove_head_node = head_node
      if remove_head_node == nil
        return nil
      end

      @head_node = remove_head_node.next_node

      if head_node != nil
        head_node.prev_node = nil
      end

      if remove_head_node == tail_node
        remove_tail
      end

      return remove_head_node
  end
```

4. **Removing the tail:**
```bash
 def remove_tail
    remove_tail_node = tail_node 
      if remove_tail_node == nil
        return nil
      end

      @tail_node = remove_tail_node.prev_node

      if tail_node != nil
        tail_node.next_node = nil
      end
      
      if remove_tail_node == head_node
        remove_head.get_value
      end 

      return remove_tail_node.get_value
  end
```

5. **Removing a any value in list:**
```bash
 def remove_value(value_to_remove)
    node_to_remove = nil
    current_node = head_node  

    while current_node != nil
      if current_node.get_value == value_to_remove  
        node_to_remove = current_node
        break
      else
        current_node = current_node.next_node
      end
    end

    if value_to_remove == nil
      return nil
    end

    if node_to_remove == head_node
      remove_head
    elsif node_to_remove == tail_node
      remove_tail
    else
      next_node = node_to_remove.next_node
      prev_node = node_to_remove.prev_node
      next_node.prev_node = prev_node
      prev_node.next_node = next_node
    end

    return node_to_remove
  end
end
```

6. 
## Recap

**_Linked Lists:_**
+ Consists of nodes each containing data and a link to the next node
+ Is a basic data structure and forms the basis for many other data structures
+ There is a single head node, acting as the first node in the list
+ Requires some maintenance to add or remove buttons
+ Quick insertion (Add very quickly with complexity is only O(1))
+ Quick deletion
+ Slow search (Slow search due to having to traverse many nodes to get to the node you are looking for)...

.

**_Doubly Linked List:_**
+ They consist of nodes containing two links to its next and previous node.
+ It has 2 pointers to be able to move in both forward and backward direction.
+ It has a pointer to a unique head node, acting as the first node in the list.
+ It has a pointer to a single tail node, which acts as the last node in the list.
+ The pointers at the beginning of the list must be updated after adding or removing the header.
+ The pointers at the end of the list must be updated after adding or removing the tail.
+ The pointers of the surrounding nodes must be updated after removing from the middle of the list.

## Compare

**Singly Linked List:**
+ Singly Linked List is less memory consuming, through the implementation we also see that the implemet is simpler, the insertion and deletion operations are also simpler.
+ It is only possible to iterate or traverse the list in one direction, so if we lose the pointer to this single list we can lose the single list in memory forever.

**Doubly Linked List:**
It is possible to iterate from both sides, the search can be faster because it can be manipulated from both sides but will consume more memory.

### Conclusion

We can use Singly Linked List in case we have little memory or memory is really expensive and need to be careful when using memory, otherwise Doubly Linked List is a suitable choice.
