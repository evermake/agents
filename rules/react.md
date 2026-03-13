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

**Rule**: Use `classnames` package for constructing `className` strings; import using default import aliased as `cn`.

```jsx
// Bad
<Block className={`btn${error ? ' red' : ''}`} />

// Bad
import clsx from 'clsx'
<Block className={clsx('btn', { red: !!error })} />

// Good
import cn from 'classnames'
<Block className={cn('btn', { red: !!error })} />
```
