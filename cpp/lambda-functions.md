# Lambda Functions (C++11)

A way of defining *anonymous* function objects *(a closure)* right at the location where it is invoked or passed as argument to a function.

```cpp
 1   2    3       4        5 
[=] () mutable throw() -> int
{
    int n = x + y;
    x = y;
    y = n;
    return n;
}
```

A lambda function has the following parts,

1. capture clause or lambda introducer 
   - [&]
   - [=]
   - [&a, b]
   - [a, b]
   - [&a, &b]
   - [=, &b]
   - [&, a]
2. parameter list or lambda declarator (optional)
3. mutation specification (optional)
4. expception specification (optional)
5. trailing return type (optional)
6. lambda body


## References
- https://docs.microsoft.com/en-us/cpp/cpp/lambda-expressions-in-cpp?view=msvc-160
