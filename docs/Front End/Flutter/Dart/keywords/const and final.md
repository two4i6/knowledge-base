# const and final
Variable declared `final` or `const` keyword can only be set once and never changed.

Subtle difference between `final` and `const`
 
## const 常量 更加严格
`const` variables must be determined at compile (and cannot be changed)

## final 
`final` variables must be determined at runtime (and cannot be changed)

note: **Class instance variables can be final**, but not const
- Use *static const* for class CONSTANTS