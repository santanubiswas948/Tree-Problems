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
import java.util.*;
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
class BSTProblem {
    List list = new ArrayList<Integer>();
    void getInOrderTraversal(Node node){
        if (node == null) return;
        else {
            inorderTraversal(node.left);
            list.add(node.val);
            inorderTraversal(node.right);
        }
    }
    public List<Integer> inorderTraversal(Node root) {
       getInOrderTraversal(root);
       return list;
    }
    public static void main(String[] args) {
        BSTProblem obj = new BSTProblem();
        Node root = new Node(10, 
        new Node(4,
            new Node(1, null, null),
            new Node(6, null, null)
            ),
        new Node(15, 
            new Node(13, null, null),
            new Node(18, null, null)
            )
        );
       System.out.println(obj.inorderTraversal(root)); // [1, 4, 6, 10, 13, 15, 18]
    }
}
```

### Problems 2: Binary Tree Preorder Traversal
```.java
import java.util.*;
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
class BSTProblem {
    List list = new ArrayList<Integer>();
    void traverseInPreOrder(Node node){
        if (node == null) return;
        else {
            list.add(node.val);
            traverseInPreOrder(node.left);
            traverseInPreOrder(node.right);
        }
    }
    public List<Integer> preOrderTraversal(Node root) {
       traverseInPreOrder(root);
       return list;
    }
    public static void main(String[] args) {
        BSTProblem obj = new BSTProblem();
        Node root = new Node(10, 
        new Node(4,
            new Node(1, null, null),
            new Node(6, null, null)
            ),
        new Node(15, 
            new Node(13, null, null),
            new Node(18, null, null)
            )
        );
       System.out.println(obj.preOrderTraversal(root)); // [10, 4, 1, 6, 15, 13, 18]
    }
}
```

### Problems 3: Binary Tree Postorder Traversal
```.java
import java.util.*;
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
class BSTProblem {
    List list = new ArrayList<Integer>();
    void traversePostOrder(Node node) {
        if (node == null) return;
        else {
            traversePostOrder(node.left);
            traversePostOrder(node.right);
            list.add(node.val);
        }
    }
    public List<Integer> postorderTraversal(Node root) {
        traversePostOrder(root);
        return list;
    }
    public static void main(String[] args) {
        BSTProblem obj = new BSTProblem();
        Node root = new Node(10, 
        new Node(4,
            new Node(1, null, null),
            new Node(6, null, null)
            ),
        new Node(15, 
            new Node(13, null, null),
            new Node(18, null, null)
            )
        );
       System.out.println(obj.postorderTraversal(root)); // [1, 6, 4, 13, 18, 15, 10]
    }
}
```
### Problems 4: How to validate a binary tree whether binary search tree or not
```.java
import java.util.*;
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
class BSTProblem {
    List<Integer> list = new ArrayList<>();
    void traverseInOrder(Node node){
        if (node == null) return;
        else {
            traverseInOrder(node.left);
            list.add(node.val);
            traverseInOrder(node.right);
        }
    }

    public boolean isValid(Node root) {
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
    public static void main(String[] args) {
        BSTProblem obj = new BSTProblem();
        Node root = new Node(10, 
        new Node(4,
            new Node(1, null, null),
            new Node(6, null, null)
            ),
        new Node(15, 
            new Node(13, null, null),
            new Node(18, null, null)
            )
        );
       System.out.println(obj.isValid(root)); // true
    }
}
```

### Problems 5: Kth smallest element in a Binary Search Tree
```.java
import java.util.*;
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
class BSTProblem {
    List<Integer> list = new ArrayList<>();
    void traverseInOrder(Node node) {
        if (node == null) return;
        else {
            traverseInOrder(node.left);
            list.add(node.val);
            traverseInOrder(node.right);
        }
    }
    public int kthSmallest(Node root, int k) {
        traverseInOrder(root);
        return list.get(k-1);
    }
    public static void main(String[] args) {
        BSTProblem obj = new BSTProblem();
        Node root1 = new Node(10, 
        new Node(4,
            new Node(1, null, null),
            new Node(6, null, null)
            ),
        new Node(15, 
            new Node(13, null, null),
            new Node(18, null, null)
            )
        );
       System.out.println(obj.kthSmallest(root1, 2)); // 4
    }
}
```

### Problems 6: Minimum Distance Between BST Nodes
```.java
import java.util.*;
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
class BSTProblem {
    List<Integer> list = new ArrayList<>();
    void traverseInOrder(Node node) {
        if (node == null) return;
        else {
            traverseInOrder(node.left);
            list.add(node.val);
            traverseInOrder(node.right);
        }
    }
    int getMinDiff(Node root) {
        traverseInOrder(root);
        // System.out.println("list:"+list+"\n");
        int min = Integer.MAX_VALUE;
        for(int i = 1; i<list.size(); i++) {
            int diff = list.get(i) - list.get(i-1);
            if (diff < min) {
                min = diff;
            }
        }
        return min;
    }
    public static void main(String[] args) {
        BSTProblem obj = new BSTProblem();
        Node root1 = new Node(10, 
        new Node(4,
            new Node(1, null, null),
            new Node(6, null, null)
            ),
        new Node(15, 
            new Node(13, null, null),
            new Node(18, null, null)
            )
        );
       System.out.println(obj.getMinDiff(root1)); //
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
### Problems 8: Count Good Nodes in Binary tree (a node P in the tree is named good if in the path from root to P there are no nodes with a value greater than P)
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
class FindGoodNodes {
    static int totalGoodNodes = 0;
    void getGoodNodes(Node node, int maxInPath){
      if (node == null) return ;
      totalGoodNodes += node.val >= maxInPath ? 1 : 0;
      int max = Math.max(maxInPath, node.val);
      getGoodNodes(node.left, max);
      getGoodNodes(node.right, max);
    }
    public static void main(String[] args) {
        FindGoodNodes obj = new FindGoodNodes();
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
        obj.getGoodNodes(root1, Integer.MIN_VALUE);
       System.out.println(totalGoodNodes); // 5
    }
}
```
### Problems 9: Evaluate Boolean Binary Tree
```
You are given the root of a full binary tree with the following properties:

Leaf nodes have either the value 0 or 1, where 0 represents False and 1 represents True.
Non-leaf nodes have either the value 2 or 3, where 2 represents the boolean OR and 3 represents the boolean AND.
The evaluation of a node is as follows:

If the node is a leaf node, the evaluation is the value of the node, i.e. True or False.
Otherwise, evaluate the node's two children and apply the boolean operation of its value with the children's evaluations.
Return the boolean result of evaluating the root node.

A full binary tree is a binary tree where each node has either 0 or 2 children.

A leaf node is a node that has zero children.
```
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
class EvaluateBT {
    boolean evaluate(Node node){
        if (node == null) return true;
        else if(node.val == 0) return false;
        else if(node.val == 1) return true;
        else if (node.val == 2) return evaluate(node.left) || evaluate(node.right);
        return evaluate(node.left) && evaluate(node.right);
    }
    public static void main(String[] args) {
        EvaluateBT obj = new EvaluateBT();
        Node root1 = new Node(2, 
        new Node(3,
            new Node(1, null, null),
            new Node(0, null, null)
            ),
        new Node(2, 
            new Node(0, null, null),
            new Node(1, null, null)
            )
        );
       System.out.println(obj.evaluate(root1)); // true
    }
}
```
### Problems 10: Balance a Binary Search Tree
```
Given the root of a binary search tree, return a balanced binary search tree with the same node values. If there is more than one answer, return any of them.

A binary search tree is balanced if the depth of the two subtrees of every node never differs by more than 1.
```
```.java
import java.util.*;

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
class BalanceBST {
    List<Integer> inOrderData = new ArrayList<>();
    void inOrderTraversal(Node node){
        if (node == null) return;
        inOrderTraversal(node.left);
        inOrderData.add(node.val);
        inOrderTraversal(node.right);
    }
    Node constructBST(int start, int end) {
        if (start > end) return null;
        int mid = (start + end)/2;

        Node node = new Node(inOrderData.get(mid), constructBST(start, mid-1), constructBST(mid + 1, end));
        return node;
    }
    public static void main(String[] args) {
        BalanceBST obj = new BalanceBST();
        Node root1 = new Node(4, 
        new Node(2,
            new Node(1, null, null),
            new Node(3, null, null)
            ),
        new Node(7, 
            new Node(5, null, null),
            new Node(6, null, null)
            )
        );
        obj.inOrderTraversal(root1);
        
       System.out.println(obj.constructBST(0, obj.inOrderData.size() - 1)); // balanced BST
    }
}
```
### Problems 11: Convert Sorted List to Binary Search Tree
```
Given the head of a singly linked list where elements are sorted in ascending order, convert it to a height-balanced binary search tree.
```
```.java
import java.util.*;

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
class Linkedlist {
  int val;
  Linkedlist next;
  Linkedlist(int val, Linkedlist next) {
     this.val = val;
     this.next = next;
  }
}
class BalanceBST {
    List<Integer> sortedList = new ArrayList<>();
    Node constructBST(int start, int end){
        if (start > end) return null;
        int mid = (start + end) / 2 ;
        Node node = new Node(
         sortedList.get(mid),
         constructBST(start, mid - 1),
         constructBST(mid + 1, end)
        );
        return node;
    }
    void getSortedList(Linkedlist node) {
        while(node != null) {
            sortedList.add(node.val);
            node = node.next;
        }
    }
    public static void main(String[] args) {
        BalanceBST obj = new BalanceBST();
        Linkedlist root = new Linkedlist(1, new Linkedlist(2, new Linkedlist(3, new Linkedlist(4, null))));
        obj.getSortedList(root);
        
       System.out.println(obj.constructBST(0, obj.sortedList.size() - 1)); // balanced BST
    }
}
```
### Problems 12: Maximum Binary Tree
```
You are given an integer array nums with no duplicates. A maximum binary tree can be built recursively from nums using the following algorithm:

Create a root node whose value is the maximum value in nums.
Recursively build the left subtree on the subarray prefix to the left of the maximum value.
Recursively build the right subtree on the subarray suffix to the right of the maximum value.
Return the maximum binary tree built from nums.
```
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
class BT {
    Node constructBT(int s, int e, int[] nums){
        if (s > e) return null;
        int max = Integer.MIN_VALUE;
        int maxIndex = -1;
        for(int i = s; i<=e; i++) {
            if (nums[i] > max) {
                max = nums[i];
                maxIndex = i;
            }
        }
        return new Node(max,
         constructBT(s, maxIndex - 1, nums),
         constructBT(maxIndex + 1, e, nums)
        );

    }
    
    Node constructMaximumBinaryTree(int[] nums) {
        return constructBT(0, nums.length - 1, nums);
    }
    public static void main(String[] args) {
            BT bt = new BT();
            Node ans = bt.constructMaximumBinaryTree(new int[]{3,2,1,6,0,5});
            System.out.println(ans);
    }
}

```
### Problems 14: Sum Root to Leaf Numbers
```
You are given the root of a binary tree containing digits from 0 to 9 only.

Each root-to-leaf path in the tree represents a number.

For example, the root-to-leaf path 1 -> 2 -> 3 represents the number 123.
Return the total sum of all root-to-leaf numbers. Test cases are generated so that the answer will fit in a 32-bit integer.

A leaf node is a node with no children.
```
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
class SumToLeafNodes {
    int sum = 0;
    void getSum(Node node, int val) {
        if (node == null) {
            sum += val;
            return;
        }
        else {
            if (node.left != null ) getSum(node.left, val*10 + node.val);
            if (node.right != null) getSum(node.right, val*10 + node.val);
            if (node.left == null && node.right == null) {
                getSum(null,  val*10 + node.val);
            }
        }
    }
    public int sumNumbers(TreeNode root) {
        getSum(root, 0);
        return sum;
    }

}
```

### Problems 15: Check Completeness of a Binary Tree
```
Given the root of a binary tree, determine if it is a complete binary tree.

In a complete binary tree, every level, except possibly the last, is completely filled, and all nodes in the last level are as far left as possible. It can have between 1 and 2h nodes inclusive at the last level h.
```
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
class Solution {
    public boolean isCompleteTree(Node root) {
        Queue<TreeNode> q = new LinkedList<>();
        q.offer(root);
        boolean flag = false;
        while(!q.isEmpty()) {
            TreeNode p = q.poll();
            if (p == null) {
                flag = true;
            } else {
                if (flag) return false;
                q.offer(p.left);
                q.offer(p.right);
            }
        }
        return true;
    }
}
```
