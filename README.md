# Tree-Problems
This is the project for all kind of tree problems

- # Binary Tree
## A tree is a binary tree if it has maximum 2 child in any level.
```
Example1: null

Example2:  2

Example3:  2
            \
              3
             
Example4:    2
            / \
           4    3
           
Example5:    2
            / \
            3  8
           / \
          4   5
          
 ``` 
 ## What is Full Binary Tree?
 Full binary tree is a binary tree which contains all nodes either leaf(no children) nodes or nodes which have 2 child nodes.
 ```
 Example:
            2
           / \
           3  5
             / \
            6   7
           / \
          8   9
 In this example all nodes either leaf nodes or have 2 children:
 Leaf nodes: 3, 6, 7
 Nodes with children: 2, 5
 ```
 
 ## What is Complete Binary Tree?
 Complete binary tree is a full binary tree which contains all nodes with 2 children except in last level and last level should
 start filling by nodes from left side.
 ```
 Examples:
            2
           / \
           3  5
          / \  / \
         9   5 6   7
        / \
       5   8
       
   above example is a Complete Binary Tree
   In this example all nodes are filled with 2 children except last level and even last level also started complete filling from left most.
   
   Below example is not complete binary tree because last level should fill up from left most without gap. Here with out filling 5,6 nodes,
   7 node is filled.
            2
           / \
           3  5
          / \  / \
         9   5 6   7
        / \       / \
       5   8     10 11
 ```
 
 ## What is Perfect Binary Tree?
 Perfect binary tree is a full binary tree which contains all nodes with 2 child nodes except the last depth nodes.In other words all leaf nodes
 are in same level
 ```
 Example:
            2
           / \
           3  5
          /\   /\
         4  6 7  9
         
 Leaf nodes: 4, 6, 7, 9
 Height of perfect binary tree if h then total nodes = (2^(h+1)) - 1
 In above example height is 2. so total nodes = (2^(2 + 1)) - 1 = 7
 ```
 ## What is Binary Search Tree?
 Binary Search Tree is a binary tree where left node is less than parent node and right node is greater than parent node in all levels.
 ```
 Example:
            2
           / \
          1   5
              /\
             7  9
 ```
       
## There are 3 types of binary tree traversal. 
 ```
   a) Pre-Order (root -> Left -> Right)
   b) Post-Order (Left -> Right -> root)
   c) In-Order (Left -> root -> Right)
```

### Problems 1: Binary Tree Inorder Traversal
```.java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    List list = new ArrayList<Integer>();
    void getInOrderTraversal(TreeNode node){
        if (node == null) return;
        else {
            inorderTraversal(node.left);
            list.add(node.val);
            inorderTraversal(node.right);
        }
    }
    public List<Integer> inorderTraversal(TreeNode root) {
       getInOrderTraversal(root);
       return list;
    }
}
```

### Problems 2: Binary Tree Preorder Traversal
```.java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    List list = new ArrayList<Integer>();
    void traverseInPreOrder(TreeNode node){
        if (node == null) return;
        else {
            list.add(node.val);
            traverseInPreOrder(node.left);
            traverseInPreOrder(node.right);
        }
    }
    public List<Integer> preOrderTraversal(TreeNode root) {
       traverseInPreOrder(root);
       return list;
    }
}
```

### Problems 3: Binary Tree Postorder Traversal
```.java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    List list = new ArrayList<Integer>();
    void traversePostOrder(TreeNode node) {
        if (node == null) return;
        else {
            traversePostOrder(node.left);
            traversePostOrder(node.right);
            list.add(node.val);
        }
    }
    public List<Integer> postorderTraversal(TreeNode root) {
        traversePostOrder(root);
        return list;
    }
}
```
### Problems 4: How to validate a binary tree whether binary search tree or not
```.java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {

    List<Integer> list = new ArrayList<>();

    void traverseInOrder(TreeNode node){
        if (node == null) return;
        else {
            traverseInOrder(node.left);
            list.add(node.val);
            traverseInOrder(node.right);
        }
    }

    public boolean isValidBST(TreeNode root) {
        traverseInOrder(root);
        for(int i = 1; i<list.size(); i++) {
            int currVal = list.get(i);
            int prevVal = list.get(i-1);
            if (currVal <= prevVal) {
                 return false;
            }
        }
        return true;
    }
}
```

### Problems 5: Kth smallest element in a Binary Search Tree
```.java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    List<Integer> list = new ArrayList<>();
    void traverseInOrder(TreeNode node) {
        if (node == null) return;
        else {
            traverseInOrder(node.left);
            list.add(node.val);
            traverseInOrder(node.right);
        }
    }
    public int kthSmallest(TreeNode root, int k) {
        traverseInOrder(root);
        return list.get(k-1);
    }
}
```

### Problems 6: Minimum Distance Between BST Nodes
```.java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    List<Integer> list = new ArrayList<>();
    void traverseInOrder(TreeNode node) {
        if (node == null) return;
        else {
            traverseInOrder(node.left);
            list.add(node.val);
            traverseInOrder(node.right);
        }
    }
    public int minDiffInBST(TreeNode root) {
        traverseInOrder(root);
        int min = Integer.MAX_VALUE;
        for(int i = 1; i<list.size(); i++) {
            int diff = list.get(i) - list.get(i-1);
            if (diff < min) {
                min = diff;
            }
        }
        return min;
    }
}
```

### Problems 7: Check whether a tree Symmetric or not
```.java
class Node {
    int val;
    Node left;
    Node right;
    Node(int val, Node left, Node right) {
      this.val = val;
      this.left = left;
      this.right = right;
    }
}
class Symmetric {
    boolean check(Node lNode, Node rNode){
         if (lNode == null && rNode == null) return true;
         else if(lNode != null && rNode != null) {
            return lNode.val == rNode.val && check(lNode.left, rNode.right) && check(lNode.right, rNode.left);
         }
         return false;
    }
    boolean isSymmetric(Node root){
      if (root == null) return true;
      return check(root.left, root.right);
    }
    public static void main(String[] args) {
        Symmetric obj = new Symmetric();
        Node root1 = new Node(2, 
        new Node(4,
            new Node(3, null, null),
            new Node(5, null, null)
            ),
        new Node(4, 
            new Node(5, null, null),
            new Node(3, null, null)
            )
        );
        
        Node root2 = new Node(2, 
        new Node(4,
            new Node(3, null, null),
            new Node(5, null, null)
            ),
        new Node(4, 
            null,
            null
            )
        );
       System.out.println(obj.isSymmetric(root1)); // true
       System.out.println(obj.isSymmetric(root2)); // false
    }
}
```
