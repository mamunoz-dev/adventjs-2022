### 120 puntos

```js
function createCube(size) {
  let cube = '';
  let i = 0;
  let j = 0;
  
  while(i < size) {
    cube = cube + ' '.repeat(size-i-1) + '/\\'.repeat(i+1) + '_\\'.repeat(size) + '\n';
    i++;
  }
  
  while(j < size) {
    cube = cube + ' '.repeat(j) + '\\/'.repeat(size - j) + '_/'.repeat(size) + '\n';
    j++;
  }
  
  return cube.replace(/\n$/, "")
}
```

### 160 puntos

```js
function createCube (size) {
  let firstHalf = '';
  let secondHalf = '';
  
  for (let i=0; i<size; i++) {
    firstHalf += `${' '.repeat(size-i-1) +
      '/\\'.repeat(i+1) +
      '_\\'.repeat(size)}\n`;
    secondHalf += `${' '.repeat(i) +
      '\\/'.repeat(size-i) +
      '_/'.repeat(size)}\n`;
  }

  return (firstHalf + secondHalf).replace(/\n$/, "");
}
```
