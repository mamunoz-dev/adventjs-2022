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
countHours = (year, holidays) => {
  return holidays.filter(day => new Date(`${year}/${day}`).getDay() % 6 !== 0).length*2;
}
```

### 122 Points
```js
countHours = (year, holidays) => {
  const WORKING_DAYS = [1, 2, 3, 4, 5];
  return holidays.filter(day => WORKING_DAYS.includes(new Date(`${year}/${day}`).getDay())).length*2;
}
```
