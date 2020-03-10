# Binary Trees

"The most important concept in computer science" - Josh Hug

**Similarities to Linked Lists**
 - Start with a linked list
 - Put the start pointer in the middle
 - Make next pointers point to the middle value in each the left and right sides
 - Continue process recursively

**Definitions:**
 - **Tree:** An ADT with a node and branches.
    - There must be exactly one path between any two nodes (no looping pointers)
 - **Rooted Tree:** One node is considered the root
    - Every node except root has exactly one parent (root has 0)
 - **Binary Tree:** Every node has 0, 1, or 2 children
 - **Binary Search Tree:** A sorted binary tree
    - Every key in the left subtree is less than the node key
    - Every key in the right subtree is greater than the node key
    - **Transitive, Complete, Antisymmetric**
        - No duplicate keys allowed
        - Must have well defined comparisons between any values (either less than or greater than)
        - If p < q and q < r, p must be less than r as well

### Binary Search
```java
public BST find(BST T, Key sk) {
    if (T == null) {
        return null;
    }
    if (sk.equals(T.key)) {
        return T;
    } else if (sk < T.key) {
        return find(T.left, sk);
    } else {
        return find(T.right, sk);
    }
}
```
 - Very fast! O(log n)

### Insert
 - Very similar algorithm to search
 - Search for item. If found, do nothing
 - If not found, create a new node and put it where it should be found

### Delete
 - Must preserve tree structure as much as possible (must find new root node!!)
 - New root node must be greater than everything in left subtree and less than everything in right subtree
    - New root is not necessarily a direct child of root node
    - Choose either predecessor or successor (must have either 0 or 1 children) and replace root node with this (Hibbard deletion)
        - The value immediately less than or greater than the node