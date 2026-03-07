**Rule**: Use `jsonc` for wrangler config, not `toml`.

---

**Rule**: Always include `nodejs_compat` in the `compatibility_flags` setting.

---

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
