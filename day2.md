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
