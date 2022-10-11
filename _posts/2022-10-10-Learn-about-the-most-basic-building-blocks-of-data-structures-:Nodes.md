# Nodes

## 1.Conceptual
### What is a nodes?
![Nodes ](https://he-s3.s3.amazonaws.com/media/uploads/1b099fd.png)

  Nodes are the fundamental building blocks of many computer science data structures. They form the basis for linked lists, stacks, queues, trees, and more.

  An individual node contains data and links to other nodes. Each data structure adds additional constraints or behavior to these features to create the desired structure.

The data contained in a node can be of many types, depending on the language you are using. It can be an integer (the number 10), but it can be a string ("ten"), decimal(5,1), an array ([5,3,4]) or nothing (null) .

### Nodes linking![Nodes linking](https://www.alphacodingskills.com/imgfiles/linked-list.PNG)


 The link or links within the node are sometimes referred to as pointers. This is because they “point” to another node.

  Typically, data structures implement nodes with one or more links. If these links are null, it denotes that you have reached the end of the particular node or link path you were previously following.

Often, due to the data structure, nodes may only be linked to a single other node. This makes it very important to consider how you implement modifying or removing nodes from a data structure.

  If you inadvertently remove the single link to a node, that node’s data and any linked nodes could be “lost” to your application. When this happens to a node, it is called an 'orphaned' node.

![Nodes linking](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQ8tHK2rB3NuKBpg7Bn988vE8t_iV5lPzmgVXD3Zkv8chE6PlSiTyP1Qx6sgy7fgrSmbo4&usqp=CAU)

  Node-C is only associated with node-B. If you want to delete node-B without deleting node-C, you cannot delete the link from node-A to node-B because that will make node-B an orphan.

  To be able to preserve node-C we will change the link in node-A to point to node-C instead of node-B.

## 2.Ideas
#### Creation of Nodes 
 Nodes are created by implementing a class that will contain node elements along with its data and pointers.

  The node's data will be specified at node creation and cannot be changed. The link will be optional on initialization and can be updated.

  At the end of the node path, the link to the next node is empty because there are no more nodes.

#### Method
  We need methods to access data and bind in node. For this we will use two getters, get_data and get_link_node.

  We only allow the button's value to be set on creation. But when we want to allow updating of the node's link, we will use a setter to modify the link_node attribute.

  
## 3.Implementation 
Below i will implement node in ruby language:
```bash
class Node
  def initialize(data, next_node = nil)
    @data = data
    @next_node = next_node
  end

  def data
    @data
  end

  def next_node
    @next_node
  end
  
  def next_node=(next_node)
    @next_node = next_node
  end
end

Object initialization:

node1 = Node.new(5, nil)
node2 = Node.new(9, node1)
node3 = Node.new(2, node2)

data_node1= node2.next_node.data
data_node2 = node3.next_node.data
data_node3 = node3.data
puts data_node1
puts data_node2
puts data_node3
```

## 4.Recap
-Nodes contain data, which can be a variety of data types.

-They also contain links to other nodes. If a node has no links, or they are all null, you have reached the end of the path you were following.

-Nodes can be orphaned if there are no existing links to them.
