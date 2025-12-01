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

    There are 4 operations that this design needs to implement in order to turn the AVLTree into a usable MultiSet: ReadInv, CheckItem, AddItem, and RemoveItem. As an AVLTree cannot store identical keys, duplicates keys are handled by incrementing the value which is stored with the key, treating it as the quantity of the item stored. This multiset differs from a mundane AVLTree as its functions need to keep this key/value relationship in mind when adding and removing items.

#### ReadInv()
    This function prints out a list of items alongside its quantity in the inventory. By using a recursive helper function to execute an inorder traversal, each item's name is printed along with its quantity. This also has the benefit of displaying each item in alphabetical order by default due to the AVLTree sorting the keys as they are put in. As this behavior is already implemented in the AVL tree's class, it can be implemented by simply calling the AVLTree's function. Since each key needs to be read once, this function would have a time complexity of O(N). Lastly, the only edge case would be checking for non-null node before continuing down either branch for recursion.
    
```
//do thing
funct() {

}
```

#### CheckItem(Item)
    This function returns the number of a given item within the inventory. By using a recursive helper function to compare keys in the AVLTree, this function descends the tree until it finds either the key or a null pointer and removes the key if it is found. As this behavior is already implemented in the AVL tree's class, it can be implemented by simply calling the AVLTree's function. As only one branch of the tree needs to be traversed, the time complexity is only O(log N). The only edge case is that 0 is returned if the item is not found in the tree.

#### AddItem(Item, Quantity)
    This function adds a number of an item to the inventory. By using a recursive helper function to compare keys in the AVLTree, this function descends the tree until it either finds the key or a null pointer and adds the item to the inventory if a null pointer is found.  This behavior is mostly implemented in the AVLTree's class, with the catch that extra funtionality must be added to increase the count of any preexisting items. Since the AVLTree's fuction for adding an item returns false if the item already exists, an if statement can be used with the operator[] overload in order to increment the number of the item by the input quantity. This function can descend the branch up to twice, which would still be a time complexity of O(log N). The aforementioned base case is that if the item is found in the inventory, its number should be increased by the input quantity

```
//do thing
funct() {

}
```

#### RemoveItem(Item, Quantity)
    This function removes a number of an item from the inventory. The logic already exists within the AVLTree class for removing an item and rebalancing the AVLTree accordingly, but removing a number of an item shouldn't remove it from the tree if there are still some of that item left over. This function will begin by running CheckItem as defined above to get the number of an item within the inventory. If the number is 0, the function returns false, otherwise it returns true. If the number is less then the quatity to be removed, AVLTree's remove item function is ran removing the key/value pair from the tree. If the number is greater then the quatity to be removed, AVLTree's operator[] overload is used to subtract the quantity from the number of that item.  Since the branch can be traversed up to twice, the time complexity would still be O(log N). The base cases are those comparisons listed above. 

```
//do thing
funct() {

}
```

---

<h4 align="center">
IV. Set Operations
</h4>

#### UnionWith(Inventory)

    This function is handy for when you defeat an enemy or open a chest taking all the loot. Two inventories need to be combind in either case. This is done with a inorder traversal implemented through a recursive helper function that runs the aforementioned AddItem function with every item to add it to the player's inventory. This would have a time complexity of O(N log N), due to the inorder traversal (N) and needing to descend a branch each time (log N). Luckily, there are no edge cases that are not handled in AddItem already.

```
//do thing
funct() {

}
```

#### IntersectionWith(Inventory)

    This function is used to filter an inventory by only returning items shared with another inventory. In game this would be used by the dev to modify loot tables, perhaps using the second inventory to restrict what can show up in the first. This would then allows for the implementation of certain perks that lift these restrictions and let players earm more from any of these restricted loot tables. This would do an inorder traversal of the target's inventory running the aforementioned CheckItem function on the player's tree with each item found in the target's tree. For each item (key), the smaller of the two values (one from CheckItem, the other directly accessed) is added along with the corresponding item to a new inventory using AddItem. The new inventory keeps track of the items shared by the two inventories. This would have a time complexity of O(N log N), due to the inorder traversal (N) and needing to descend a branch twice each time (log N). There are no edge cases beyond checking for child nodes before engaging in recursion.

```
//do thing
funct() {

}
```

---

<h4 align="center">
V. Extension Feature
</h4>

    One last capability is neccisary for this MultiSet. It needs a function able to check if one inventory contains every single item at a greater quantity than what the other inventory has. If every item exists at a greater quantity, then the difference between the two inventories should be returned. This would be useful for crafting and quests, and shopping, which all require a check. This function should be run from the subtracting inventory (the list of items being removed).
#### UseInventory(Inventory)

    This function does an inorder traversal (using recursion) of the current inventory running CheckItem for every key. If the returned value is less than the value of the current item, the function immediately returns false all the way up the chain of recursion. If the function manages to complete without termination, another inorder traversal of the same inventory is done, with each item and its quantity being removed using Remove item. Then the function would return true. The time complexity would be O(N log N), due to the inorder traversal (N) and needing to descend a branch twice each time (log N). An entire inorder traversal is done to handle the edge case where the subtracting inventory is bigger.

```
//do thing
funct() {

}
```

---

<h4 align="center">
VI. UML Diagram / Abstraction Boundary
</h4>

<div align="center">

| Inventory   |
| -------- |
| + AVLNode* root |
| -------------------------------------- |
| + string ReadInv() |
| - ReadHelper(AVLNode*: Node) |
| + size_t CheckItem(string: Item) |
| + void AddItem(string: Item, size_t: Quantity) |
| + RemoveItem(string: Item, size_t: Quantity) |
| + UnionWith(inventory: Inventory) |
| - UnionHelper(AVLNode*) |
| + IntersectionWith(inventory: Inventory) |
| - IntersectionHelper(AVLNode*: Node) |
| + bool UseInventory(inventory: Inventory) |
| - bool CheckHelper(AVLNode*: Node) |
| - void RemoveHelper(AVLNode*: Node) |

</div>

---

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
