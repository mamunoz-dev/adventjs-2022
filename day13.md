# Challenge #13: Backups for Santa Claus files

### Cognitive Complexity: 1 (>2000 ops/s)

```js
function getFilesToBackup(lastBackup, changes) {
    return [...new Set(changes
        .filter(files => files[1] > lastBackup)
        .map(files => files[0])
        .sort((a,b) => a - b)
    )];
}
```
