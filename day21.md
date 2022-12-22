#

### Cognitive Complexity: 1 (> 2000 ops/sec)

```js
function printTable(gifts) {
  const repeat = (char, times) => char.repeat(times);
  const cell = (item, max) => `${item.padEnd(max)}`;
  
  gifts = gifts.map(({name, quantity}) => 
                    ({ name, quantity: quantity.toString() }));
  
  const [ maxGift, maxQuantity ] = gifts.reduce((acc, curr) => {
   return [ Math.max(acc[0], curr.name.length), 
            Math.max(acc[1], curr.quantity.length) ];
  }, [4, 8]);

  return '' +
    `${repeat('+', maxGift + maxQuantity + 7)}\n` +
    `| ${cell('Gift', maxGift)} | ${cell('Quantity', maxQuantity)} |\n` +
    `| ${repeat('-', maxGift)} | ${repeat('-', maxQuantity)} |\n` +
    gifts
      .map(({ name, quantity }) => 
           `| ${cell(name, maxGift)} | ${cell(quantity, maxQuantity)} |`)
      .reduce((acc, gift) => acc + gift + '\n', '') +
    repeat('*', maxGift + maxQuantity + 7);
}
```
