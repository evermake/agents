---
alwaysApply: true
---

**Rule**: Use default `React` export for accessing React APIs and types.

```ts
// Bad
import { useState, type ReactElement } from 'react'

function Counter(): ReactElement {
  const [count, setCount] = useState(0)
  // ...
}

// Good
import React from 'react'

function Counter(): React.ReactElement {
  const [count, setCount] = React.useState(0)
  // ...
}
```
