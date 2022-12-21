### 300 puntos (>2000 ops/sec, Complejidad Cognitiva: 1)

```js
function sortToys(toys, positions) {
  return toys
    .map((toy, i) => [positions[i], toy])
    .sort((a, b) => a[0] - b[0])
    .map(toy => toy[1])
}
```

### 300 puntos (>2000 ops/sec, Complejidad Cognitiva: 1)

```js
function sortToys(toys, positions) {
  return [...positions]
    .sort((a, b) => a - b)
    .map(v => toys[positions.indexOf(v)])
}
```
