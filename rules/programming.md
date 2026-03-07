**Rule**: Keep statements nesting to minimum; return or throw early.

```js
// Bad
function welcomeMessage(name, age) {
  if (age >= 18) {
    if (age > 24) {
      throw new Error('Too old.')
    } else {
      return `Yo, welcome, ${name}!`
    }
  } else {
    throw new Error('Too young.')
  }
}

// Good
function welcomeMessage(name, age) {
  if (age < 18) {
    throw new Error('Too young.')
  }
  if (age > 24) {
    throw new Error('Too old.')
  }
  return `Yo, welcome, ${name}!`
}
```

**More on this**:
- ["If. Then. Throw. Else. WTF?" by Yegor Bugayenko](https://www.yegor256.com/2015/01/21/if-then-throw-else.html)
- https://softwareengineering.stackexchange.com/a/18473

---

**Rule**: Use full option names for CLI commands; do not use shorthands.

```sh
# Bad
taze -wrI
git branch -m 'new-name'

# Good
taze --write --recursive --interactive
git branch --move 'new-name'
```

**Exception**: This is OK to use shorthands for one-off tasks that will not persist in a project.
