### 300 puntos (Complejidad Cognitiva: 1)

```js
function getFilesToBackup(lastBackup, changes) {
    return [...new Set(changes
        .filter(files => files[1] > lastBackup)
        .map(files => files[0])
        .sort((a,b) => a - b)
    )];
}
```
