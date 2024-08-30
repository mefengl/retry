# retry

js

```js
function retry(fn, attempts = 3, delay = 3000) {
  return async (...args) => {
    for (let i = 0; i < attempts; i++) {
      try {
        return await fn(...args)
      }
      catch (e) {
        if (i < attempts - 1)
          await new Promise(r => setTimeout(r, delay))
        else throw e
      }
    }
  }
}
```

example

```js
const fetchDataWithRetry = retry(fetchData)
```

ts

```ts
function retry(fn: any, attempts = 3, delay = 3000) {
  return async (...args: any) => {
    for (let i = 0; i < attempts; i++) {
      try {
        return await fn(...args)
      }
      catch (e) {
        if (i < attempts - 1)
          await new Promise(r => setTimeout(r, delay))
        else throw e
      }
    }
  }
}
```
