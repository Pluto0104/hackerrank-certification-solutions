### Maximizing the Final Element

Given an array of integers, perform certain operations in order to satisfy some constraints. The constraints are as follows:

- The first array element must be 1.
- For all other elements, the difference between adjacent integers must not be greater than 1. In other words, for 1 ≤ i < n, arr[i] - arr[i- 1] ≤ 1.

To accomplish this, the following operations are available:

- Rearrange the elements in any way.
- Reduce any element to any number that is at least 1.

What is the maximum value that can be achieved for the final element of the array by following these operations and constraints?

#### Example

arr = [3, 1, 3, 4]

1. Subtract 1 from the first element, making the array [2, 1, 3, 4].
2. Rearrange the array into [1, 2, 3, 4].
3. The final element's value is 4, the maximum value that can be achieved. Therefore, the answer is 4.

#### Function Description

Complete the function getMaxValue in the editor below.

getMaxValue has the following parameter:

- int arr[n]: an array of integers

Returns:

- int: the maximum value that can be achieved for the final element of the array given the conditions above

#### Constraints

```
1 ≤ n ≤ 10^5
1 ≤ arr[i] ≤ 10^9
```

Input Format For Custom Testing

#### ▾ Sample Case 0

- Sample Input For Custom Testing

- Sample Output

  ```
  3
  ```

#### Explanation

These elements can be rearranged to become [1, 2, 2, 3], which results in a maximum value of 3 for the final element. Notice how this array follows the constraints that (1) the first element is 1, and (2) the difference between each pair of adjacent integers is no more than 1.

#### ▾ Sample Case 1

- Sample Input For Custom Testing

- Sample Output

  ```
  4
  ```

#### Explanation

These elements can be rearranged to become [2, 3, 3, 5]. Then, the heights can be adjusted to become [1, 2, 3, 4]. Therefore, the maximum value of the final element is 4.

### Solution

```js
function getMaxValue(arr) {
  // Write your code here
  const n = arr.length;
  arr.sort((a, b) => a - b);
  if (arr[0] !== 1) {
    arr[0] = 1;
  }

  for (let i = 1; i < n; i++) {
    if (arr[i] - arr[i - 1] > 1) {
      arr[i] = arr[i - 1] + 1;
    }
  }
  return arr[n - 1];
}
```
