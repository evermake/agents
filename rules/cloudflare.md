---
alwaysApply: true
---

## Workers

**Rule**: Make sure everything that depends on a worker's environment gets re-created per request, since worker's configuration may change dynamically.

```js
// Bad
import { env } from 'cloudflare:workers'
import { SomeClient } from 'some-api'

const client = new SomeClient({ key: env.API_KEY })

export default {
  fetch(request, env) {
    // ...
  }
}

// Good
import { SomeClient } from 'some-api'

export default {
  fetch(request, env) {
    const client = new SomeClient({ key: env.API_KEY })
    // ...
  }
}
```

---

**Rule**: Always auto-generate types for worker's environment, e.g. using `wrangler types`. Do not maintain it manually.

## D1

**Rule**: Follow these conventions when naming a database:

- Lowercase alphanumeric (a-z, 0-9) separated with dashes (-)
- Format is `<project>-<db>-<env>`
  - `<project>` — name of a project
  - `<db>` — purpose of the database in the project (can be omitted)
  - `<env>` — worker environment that uses the database, e.g. `prod`, `stage`, `dev`
- Examples: `superstore-customer-data-prod`, `movies-dev`
