# Data Structures: Linked List
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

####And some other operations, we will update later.

## IV. Recap

Linked Lists:
+ Consists of nodes each containing data and a link to the next node
+ Is a basic data structure and forms the basis for many other data structures
+ There is a single head node, acting as the first node in the list
+ Requires some maintenance to add or remove buttons
+ Quick insertion (Add very quickly with complexity is only O(1))
+ Quick deletion
+ Slow search (Slow search due to having to traverse many nodes to get to the node you are looking for)...
