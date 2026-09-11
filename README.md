# LeetCode 162 - Find Peak Element

## Problem

A peak element is an element that is strictly greater than its neighboring elements.

Given an integer array `nums`, find a peak element and return its index.

You may assume that `nums[-1]` and `nums[n]` are both considered to be negative infinity.

The solution must run in **O(log n)** time.

---

## Example 1

**Input:**

```text
nums = [1,2,3,1]
```

**Output:**

```text
2
```

**Explanation:**

The element `3` is greater than both of its neighbors:

```text
1 < 2 < 3 > 1
```

Therefore, index `2` is a peak.

---

## Example 2

**Input:**

```text
nums = [1,2,1,3,5,6,4]
```

**Output:**

```text
5
```

**Explanation:**

The element `6` is greater than both neighboring elements `5` and `4`.

Index `5` is a valid peak.

There can be more than one peak, so returning any valid peak index is acceptable.

---

## Approach

The main idea is to use **Binary Search**.

Instead of checking every element, compare the middle element with the element immediately to its right.

Let:

```text
mid = (left + right) // 2
```

### Case 1: `nums[mid] > nums[mid + 1]`

This means we are moving downward from `mid`.

Therefore, a peak must exist at `mid` or somewhere on the **left side**.

So:

```text
right = mid
```

### Case 2: `nums[mid] < nums[mid + 1]`

This means the array is increasing at `mid`.

Therefore, there must be a peak somewhere on the **right side**.

So:

```text
left = mid + 1
```

Continue until:

```text
left == right
```

At that point, `left` is the index of a peak element.

---

## Algorithm

1. Set `left = 0`.
2. Set `right = len(nums) - 1`.
3. While `left < right`:

   * Calculate `mid`.
   * Compare `nums[mid]` and `nums[mid + 1]`.
   * If `nums[mid] > nums[mid + 1]`, move `right` to `mid`.
   * Otherwise, move `left` to `mid + 1`.
4. Return `left`.

---

## Example Walkthrough

For:

```text
nums = [1,2,3,1]
```

Initially:

```text
left = 0
right = 3
```

Calculate:

```text
mid = 1
```

Compare:

```text
nums[1] = 2
nums[2] = 3
```

Since:

```text
2 < 3
```

the peak must be on the right side.

So:

```text
left = 2
```

Now:

```text
left = 2
right = 3
```

Calculate:

```text
mid = 2
```

Compare:

```text
nums[2] = 3
nums[3] = 1
```

Since:

```text
3 > 1
```

the peak can be at index `2`.

So:

```text
right = 2
```

Now:

```text
left == right == 2
```

Return:

```text
2
```

---

## Time Complexity

**O(log n)**

Binary search eliminates approximately half of the search space during every iteration.

---

## Space Complexity

**O(1)**

Only a few variables such as `left`, `right`, and `mid` are used.

---

## Key Concepts

* Binary Search
* Arrays
* Two Pointers
* Comparing neighboring elements
* Search Space Reduction

---

## Important Point

The problem does **not** require finding the highest element in the entire array.

It only asks for **any valid peak**.

For example:

```text
[1,2,1,3,5,6,4]
```

has two peaks:

```text
2
```

and

```text
6
```

So either peak index can be returned.

---

## LeetCode Details

* **Problem Number:** 162
* **Problem Name:** Find Peak Element
* **Difficulty:** Medium
* **Topics:** Array, Binary Search
* **Language:** Python

---

## What I Learned

This problem helped me understand how binary search can be used even when the array is **not sorted**.

Instead of searching for a specific value, we use the relationship between neighboring elements to decide which half of the array contains a peak.

The main idea is that when the array is increasing, a peak exists to the right, and when it is decreasing, a peak exists at or to the left.

---

## Author

T.Nandhini
