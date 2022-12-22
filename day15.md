### Cognitive Complexity: 1 (>1000 ops/s)

```js
function decorateTree(base) {
  const dir = {
    'PP': 'P',
    'BB': 'B',
    'RR': 'R',
    'BP': 'R',
    'RP': 'B',
    'BR': 'P',
    'PB': 'R',
    'PR': 'B',
    'RB': 'P'
  }
  
  const tree = [base.split(' ')];
  let upRow = tree[0];
  
  while(upRow.length > 1) {
    upRow = upRow
      .map((elm, i) => dir[`${elm}${tree[0][i+1]}`])
      .filter(elm => elm);
    tree.unshift(upRow);
  }
  
  return tree.map(elm => elm.join(' '));
}
```
