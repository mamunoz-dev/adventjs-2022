# Challenge #2: Nobody wants to do extra hours at work

### Cognitive Complexity: 1 (>2000 ops/s)

```js
function countHours(year, holidays) {
  return holidays.filter(day => {
    return new Date(`${year}/${day}`).getDay() % 6 !== 0;
  }).length*2;
}
```
