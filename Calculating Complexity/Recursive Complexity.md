
>https://stackoverflow.com/questions/13467674/determining-complexity-for-recursive-functions-big-o-notation

1. `T(n) = T(n-1) + 1` It means that the time it takes for the method to finish is equal to the same method but with n-1 which is `T(n-1)` and we now add `+ 1` because it's the time it takes for the general operations to be completed (except `T(n-1)`). Now, we are going to find `T(n-1)` as follow: `T(n-1) = T(n-1-1) + 1`. It looks like we can now form a function that can give us some sort of repetition so we can fully understand. We will place the right side of `T(n-1) = ...` instead of `T(n-1)` inside the method `T(n) = ...` which will give us: `T(n) = T(n-1-1) + 1 + 1` which is `T(n) = T(n-2) + 2` or in other words we need to find our missing `k`: `T(n) = T(n-k) + k`. The next step is to take `n-k` and claim that `n-k = 1` because at the end of the recursion it will take exactly O(1) when `n<=0`. From this simple equation we now know that `k = n - 1`. Let's place `k` in our final method: `T(n) = T(n-k) + k` which will give us: `T(n) = 1 + n - 1` which is exactly `n` or `O(n)`.

```c++
int recursiveFun1(int n)
{
    if (n <= 0)
        return 1;
    else
        return 1 + recursiveFun1(n-1);
}
```



3. `T(n) = T(n/5) + 1` as before, the time for this method to finish equals to the time the same method but with `n/5` which is why it is bounded to `T(n/5)`. Let's find `T(n/5)` like in 1: `T(n/5) = T(n/5/5) + 1` which is `T(n/5) = T(n/5^2) + 1`. Let's place `T(n/5)` inside `T(n)` for the final calculation: `T(n) = T(n/5^k) + k`. Again as before, `n/5^k = 1` which is `n = 5^k` which is exactly as asking what in power of 5, will give us n, the answer is `log5n = k` (log of base 5). Let's place our findings in `T(n) = T(n/5^k) + k` as follow: `T(n) = 1 + logn` which is `O(logn)`
```c++
int recursiveFun3(int n)
{
    if (n <= 0)
        return 1;
    else
        return 1 + recursiveFun3(n/5);
}
```

\

4. `T(n) = 2T(n-1) + 1` what we have here is basically the same as before but this time we are invoking the method recursively 2 times thus we multiple it by 2. Let's find `T(n-1) = 2T(n-1-1) + 1` which is `T(n-1) = 2T(n-2) + 1`. Our next place as before, let's place our finding: `T(n) = 2(2T(n-2)) + 1 + 1` which is `T(n) = 2^2T(n-2) + 2` that gives us `T(n) = 2^kT(n-k) + k`. Let's find `k` by claiming that `n-k = 1` which is `k = n - 1`. Let's place `k` as follow: `T(n) = 2^(n-1) + n - 1` which is roughly `O(2^n)`

```c++
void recursiveFun4(int n, int m, int o)
{
    if (n <= 0)
    {
        printf("%d, %d\n",m, o);
    }
    else
    {
        recursiveFun4(n-1, m+1, o);
        recursiveFun4(n-1, m, o+1);
    }
}
```


5. `T(n) = T(n-5) + n + 1` It's almost the same as 4 but now we add `n` because we have one `for` loop. Let's find `T(n-5) = T(n-5-5) + n + 1` which is `T(n-5) = T(n - 2*5) + n + 1`. Let's place it: `T(n) = T(n-2*5) + n + n + 1 + 1)` which is `T(n) = T(n-2*5) + 2n + 2)` and for the k: `T(n) = T(n-k*5) + kn + k)` again: `n-5k = 1` which is `n = 5k + 1` that is roughly `n = k`. This will give us: `T(n) = T(0) + n^2 + n` which is roughly `O(n^2)`.
```c++
int recursiveFun5(int n)
{
    for (i = 0; i < n; i += 2) {
        // do something
    }

    if (n <= 0)
        return 1;
    else
        return 1 + recursiveFun5(n-5);
}
```