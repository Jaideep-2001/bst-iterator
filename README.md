# bst-iterator
todays task
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
public class BSTIterator {
    Stack<TreeNode> stack;

    public BSTIterator(TreeNode root) {
        stack = new Stack<>();
        getLeftMostLeaf(root, stack);
    }

    public boolean hasNext() {
        return !stack.isEmpty();
    }

    public int next() {
        TreeNode node = stack.pop();
        if (node.right != null) getLeftMostLeaf(node.right, stack);
        return node.val;
    }
    
    private TreeNode getLeftMostLeaf(TreeNode node, Stack<TreeNode> stack) {
        if (node == null) return null;
        stack.push(node);
        while (node.left != null) {
            node = node.left;
            stack.push(node);
        }
        return node;
    }
}
