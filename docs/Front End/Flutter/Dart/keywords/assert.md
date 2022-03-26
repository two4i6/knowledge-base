# Assertions
During development use an assert to disrupt normal execution.
- They are removed from release build automatically.
- If the statement passed to the assert fails, then program execution stops.

```dart
assert(text != null);
assert(number < 100);
assert(urlString.startWiht('http'));

// with message
assert(text != null, "text not null")
```