### 300 puntos (> 2000 ops/sec, Complejidad Cognitiva: 1)

```js
function fixLetter(letter) {
  return letter
    .trim()
    .replace(/[\s]+|[?]+/g, v => v.charAt(0))
    .replace(/[Ss]anta [Cc]laus/g, 'Santa Claus')
    .replace(/([\.?!] [a-z]|^[a-z])/g, (v) => v.toUpperCase())
    .replace(/[a-z]$/g, (v) => `${v}.`)
    .replace(/\s*([,\.\?])\s*/g, "$1 ")
    .trim()
}
```
