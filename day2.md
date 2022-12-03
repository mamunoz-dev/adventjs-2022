### 121 Points

```js
function countHours(year, holidays) {
  return holidays.reduce((acc, currentValue) => {
    const dayOfWeek = new Date(`${currentValue}/${year}`).getDay();
    
    if (dayOfWeek === 0 || dayOfWeek === 6) {
      return acc;
    }
    
    return acc + 2;
  }, 0);
}
```

### 122 Points

```js
countHours = (year, holidays) => {
  return holidays.reduce((acc, currentValue) => new Date(`${currentValue}/${year}`).getDay() % 6 ? acc+2 : acc, 0);
} 
```

### 122 Points

```js
countHours = (y, h) => {
  return h.filter(c => new Date(`${y}/${c}`).getDay() % 6 !== 0).length*2;
} 
```

### 122 Points
```js
countHours = (y, h) => {
  return h.filter(c => [1,2,3,4,5].includes(new Date(`${y}/${c}`).getDay())).length*2;
} 
```
