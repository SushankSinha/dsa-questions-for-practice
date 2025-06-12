### Question - [Climbing Stairs](https://leetcode.com/problems/climbing-stairs)  
**Intuitive Approach**

```js
var climbStairs = function (n) {
    if (n === 1 || n === 2 || n === 3) {
        return n;
    }

    function factorial(int) {
        if (int === 0 || int === 1) {
            return 1;
        } 
        let res = 1;
        for (let i = 2; i <= int; i++) {
            res *= i;
        }
        return res;
    }

    let output = 0;
    for (let i = 0; i <= Math.floor(n / 2); i++) {
        let j = n - 2 * i;
        if (j < 0) break;
        let int = i + j;
        let permutations = factorial(int) / (factorial(i) * factorial(j));
        output += permutations;
    }
    return output;
};


Time Compplexity - O(n^2)
Space Complexity - O(1)
``` 

**Optimized Approach**

```js
var climbStairs = function (n) {
if(n===1||n===2) return n;

  let firstStep = 1;
  let res = 2;

  for (i=3;i<=n;i++){
      let sum = firstStep + res;
      firstStep = res;
      res = sum;
  }

  return res;
}

Time Compplexity - O(n)
Space Complexity - O(1)
```
