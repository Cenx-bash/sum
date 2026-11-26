# Binary Search Tree Assignment

**BST Rule:** Smaller values go left; larger values go right.  
**Deletion Rule:** If the node has two children, replace it with its **in-order successor** (smallest value in its right subtree).

## 1. Insertion

### Item 1: Insert `20, 10, 30, 5, 15, 25, 35`

#### After inserting `20`
```text
20
```

#### After inserting `10`
```text
  20
 /
10
```

#### After inserting `30`
```text
  20
 /  \
10  30
```

#### After inserting `5`
```text
    20
   /  \
 10   30
 /
5
```

#### After inserting `15`
```text
    20
   /  \
 10   30
 / \
5 15
```

#### After inserting `25`
```text
    20
   /  \
 10   30
 / \  /
5 15 25
```

#### After inserting `35`
```text
    20
   /  \
 10   30
 / \  / \
5 15 25 35
```

**Final BST after Item 1:**
```text
        20
       /  \
     10    30
    / \   / \
   5  15 25 35
```

### Item 2: Insert `18` into the BST above

**Explanation:**  
`18 < 20` → go left to `10`.  
`18 > 10` → go right to `15`.  
`18 > 15` → go right. The right child of `15` is empty, so insert `18` there.

```text
        20
       /  \
     10    30
    / \   / \
   5  15 25 35
       \
       18
```

### Item 3: Insert `7, 17, 28` into the BST above

**Insert `7`:**  
`7 < 20` left → `7 < 10` left → `7 > 5` right.  
So `7` becomes the right child of `5`.

**Insert `17`:**  
`17 < 20` left → `17 > 10` right → `17 > 15` right → `17 < 18` left.  
So `17` becomes the left child of `18`.

**Insert `28`:**  
`28 > 20` right → `28 < 30` left → `28 > 25` right.  
So `28` becomes the right child of `25`.

**Final BST after all insertions in Items 1–3:**
```text
          20
        /    \
      10      30
     /  \    /  \
    5   15  25  35
     \    \   \
      7   18  28
          /
         17
```

## 2. Traversals

Using the final BST after all insertions in Items 1–3:

| Traversal | Arrangement |
|---|---|
| **Pre-order** | `20, 10, 5, 7, 15, 18, 17, 30, 25, 28, 35` |
| **In-order** | `5, 7, 10, 15, 17, 18, 20, 25, 28, 30, 35` |
| **Post-order** | `7, 5, 17, 18, 15, 10, 28, 25, 35, 30, 20` |

**Notes:**  
- Pre-order = root → left → right  
- In-order = left → root → right  
- Post-order = left → right → root  
- The in-order traversal is sorted because the tree is a BST.

## 3. Searching

### Search for `15` in the BST from Item 1

BST from Item 1:
```text
        20
       /  \
     10    30
    / \   / \
   5  15 25 35
```

**Path taken:**
```text
20 → 10 → 15
```

**Result:** `15` is found.

### Search for `22` in the BST from Item 1

**Path taken:**
```text
20 → 30 → 25 → null
```

**Step-by-step:**  
- `22 > 20` → go right to `30`.  
- `22 < 30` → go left to `25`.  
- `22 < 25` → go left, but `25` has no left child.

**Result:** `22` is **not found**.

### Search for `28` in the BST from Item 3

BST from Item 3:
```text
          20
        /    \
      10      30
     /  \    /  \
    5   15  25  35
     \    \   \
      7   18  28
          /
         17
```

**Path taken:**
```text
20 → 30 → 25 → 28
```

**Result:** `28` is found.

## 4. Deletion

### Delete `10` from the BST from Item 1

**BST before deletion:**
```text
        20
       /  \
     10    30
    / \   / \
   5  15 25 35
```

**Explanation:**  
Node `10` has two children: `5` and `15`.  
The in-order successor of `10` is the smallest value in its right subtree, which is `15`.  
Replace `10` with `15`, then remove the original `15` node.

**Resulting BST:**
```text
        20
       /  \
     15    30
    /     / \
   5    25 35
```

### Delete `20` from the BST from Item 3

**BST before deletion:**
```text
          20
        /    \
      10      30
     /  \    /  \
    5   15  25  35
     \    \   \
      7   18  28
          /
         17
```

**Explanation:**  
Node `20` has two children.  
The in-order successor of `20` is the smallest value in its right subtree, which is `25`.  
Replace `20` with `25`, then delete the original `25` node. Since original `25` had a right child `28`, `28` takes its place.

**Resulting BST:**
```text
          25
        /    \
      10      30
     /  \    /  \
    5   15  28  35
     \    \
      7   18
          /
         17
```

### Delete `30` from the BST from Item 3

**BST before deletion:**
```text
          20
        /    \
      10      30
     /  \    /  \
    5   15  25  35
     \    \   \
      7   18  28
          /
         17
```

**Explanation:**  
Node `30` has two children: `25` and `35`.  
The in-order successor of `30` is the smallest value in its right subtree, which is `35`.  
Replace `30` with `35`, then remove the original `35` node.

**Resulting BST:**
```text
          20
        /    \
      10      35
     /  \    /
    5   15  25
     \    \   \
      7   18  28
          /
         17
```

### Delete `12` from the BST from Item 1

**BST from Item 1:**
```text
        20
       /  \
     10    30
    / \   / \
   5  15 25 35
```

**Search path for `12`:**
```text
20 → 10 → 15 → null
```

**Explanation:**  
`12 < 20` → go left to `10`.  
`12 > 10` → go right to `15`.  
`12 < 15` → go left, but `15` has no left child.  
Therefore, `12` is not in the tree.

**Result:** `12` is **not found**, so the BST remains unchanged:
```text
        20
       /  \
     10    30
    / \   / \
   5  15 25 35
```
