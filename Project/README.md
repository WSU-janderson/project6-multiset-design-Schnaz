<h2 align="center">
Project 6 - Multiset Design
</h2>

<h6 align="center">
Adam Hume <br>
CEG 3100 - Data Structures & Algorithms <br>
Dayton, Ohio <br>
hume.14@wright.edu
</h6>

---

<h4 align="center">
I. Introduction
</h4>


    An inventory was designed for a new text based adventure in the works known as Bork (a pun on the name of Zork). The game has no max capacity for the inventory, so the inventory gets really large rather quick. As this is a text based adventure, items are not called by a numerical index but by a string. In addition the number of each item has to be stored. The inventory system utilizes an AVL Tree to store each item in alphabetical order. Items are stored in the tree using the item name as the key and the number of the item as the stored value.

---


<h4 align="center">
II. Design Philosophy
</h4>

    This game needed an inventory system that can hold an item name to be referenced through text, and a number to contain the number of the item the player carries. Additionally, the inventory had to maintain some sort of order so that an item can be easily found when a user checks their inventory. An AVL tree was chosen to handle the inventory as it keeps all the items in alphabetical order, which is rather handy as the inventory gets really large late game. Readability was prioritized over speed when choosing the datastructure, as maintaining the inventory in an organized format is much more important. Text based games are not affected adversely by lag (and are not performance heavy on top of that), but having to sift through an extensive unorderly inventory would undoubtedly ruin a player's experience. The primary user of this AVL tree is the player, not the developer, so having a readable inventory is vital. 

---

<h4 align="center">
III. Core Operations
</h4>

    There are 4 operations that this design needs to implement:

#### Inventory.ReadInv()
    This function prints out a list of items alongside its quantity in the inventory. Using a recursive helper function to execute an inorder traversal, each item's name is printed along with its quantity. This also has the benefit of displaying each item in alphabetical order by default due to the AVLTree sorting the keys as they are put in. Since each key needs to be read once, this function would have a time complexity of O(N). Lastly, the only edge case would be checking for non-null node before continuing down either branch for recursion.
    
```
//do thing
funct() {

}
```

#### Inventory.CheckItem(Item)
    This function returns the number of a given item within the inventory. By comparing keys in the AVLTree This function recusively descends the tree until it either finds the key or a null pointer. This function is already implemented in the AVL tree's class
- The Time complexity is O(log N)
- The only edge case is that 0 is returned if the item is not found in the tree
#### AddItem(Item, Quantity)

- This adds X ammount of a certain item to a player's inventory
- This runs the above function to check if 
#### RemoveItem(Item, Quantity)


<h4 align="center">
IV. Set Operations
</h4>

<p>
    
</p>

<h4 align="center">
V. Extension Feature
</h4>

<p>
    
</p>

<h4 align="center">
VI. UML Diagram / Abstraction Boundary
</h4>

<p>
    
</p>

<h4 align="center">
VII. Trade-off Analysis
</h4>

<p>
    
</p>

<h4 align="center">
VIII. Alternative Design Sketch
</h4>

<p>
    
</p>

<h4 align="center">
IX. Evaluation Plan
</h4>

<p>
    
</p>

<h4 align="center">
X. Conclusion / Reflection
</h4>

<p>
    
</p>
