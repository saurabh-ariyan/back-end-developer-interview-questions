```display: a.props ? "block" : "none" === display : !a.props && none```
- the `&&` operator check the truthiness of the right argument: 
   - if true: return left
   - if false: return null 
Hence it can act as a ternary operator with the false argument being null. 
