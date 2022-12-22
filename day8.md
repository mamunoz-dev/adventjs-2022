# Challenge #8: We need a mechanic!

### Cognitive Complexity: 1 (>3000 ops/s)

```js
function checkPart(part) {
  return [...part.slice(0, part.length/2)]
    .every((_, i, __, l=part.length-i) => 
      part[i] === part[l-1] ||
      part[i] === part[l-2] || 
      part[i+1] === part[l-1]
  )
}
```
