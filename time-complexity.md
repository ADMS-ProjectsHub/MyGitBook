# Time Complexity?

{% hint style="success" %}
**Time complexity** is a way to describe **how the runtime of an algorithm increases** with the size of the input (usually denoted as `n`). It helps us estimate how efficient an algorithm is, especially for large inputs.
{% endhint %}

## Common Big-O Notations

| Notation       | Meaning                                                           | Example                         |
| -------------- | ----------------------------------------------------------------- | ------------------------------- |
| **O(1)**       | Constant time – runs in the same time regardless of input size    | Accessing array index: `arr[5]` |
| **O(log n)**   | Logarithmic time – input size doubles, but operations grow slowly | Binary search                   |
| **O(n)**       | Linear time – grows proportionally with input                     | Simple for loop                 |
| **O(n log n)** | Linearithmic time – efficient sorting algorithms                  | Merge Sort, Quick Sort          |
| **O(n²)**      | Quadratic time – nested loops                                     | Bubble Sort, Insertion Sort     |
| **O(2ⁿ)**      | Exponential time – grows very fast                                | Recursive Fibonacci             |
| **O(n!)**      | Factorial time – used in permutations, backtracking               | Brute-force permutations        |
