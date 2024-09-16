---
layout: post
title: Binary Search Tree
subtitle: Data structure
cover-img: /assets/img/path.jpg
thumbnail-img: /assets/img/BST.png
share-img: /assets/img/path.jpg
tags: [algorithms, data structure]
author: Bruce Wang
---

## Binary Search Tree
A `binary search tree` is a binary tree in which every node fits a specific ordering property: all left descendents <= n < all right descendents. This must be true for each node n.

## definition
A binary search tree(BST), a special form of binary tree, satifies the binary search property:
- The value of the left child is less than the value of the parent node
- The value of the right child is greater than or equal to the value of the parent node

## Time complexity
- Insertion: O(logn)
- Deletion: O(logn)
- Search: O(logn)
- Traversal: O(n)
## Space complexity: 
- O(n)

Here is a example of a binary search tree.
![Binary Search Tree](/assets/img/BST.png)

Like a binary tree, we can traverse a binary search tree in three different ways:
- inorder traversal : output values will be in `ascending order`.
- preorder traversal
- postorder traversal

## Implementation
```c++
class TreeNode{
public:
    int data;
    TreeNode* left;
    TreeNode* right;
    TreeNode(int d){
        data = d;
        left = nullptr;
        right = nullptr;
    }
};

void InorderTraverse(TreeNode* root){
    if(root == nullptr) return;

    InorderTraverse(root->left);
    cout << root->data << " ";
    InorderTraverse(root->right);
}
```

## Questions
- [Validate BST](https://leetcode.com/problems/validate-binary-search-tree/)

Solution:

```c++
class solution{
private:
    bool validBST(TreeNode* node, int min, int max){
        // base case. current node is null
        if(node == nullptr) return true;
        // check if the current node is in the range
        if(node->data <= min || node->data > max) return false;

        return validBST(node->left, min, node->data) && 
               validBST(node->right, node->data, max);
    }
public:
    bool isValidBST(TreeNode* root) {
        // for each node, check if it's in the range
        return validBST(root, INT_MIN, INT_MAX);
    }
};
```