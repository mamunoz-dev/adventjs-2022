### Part 1

```js
/*
const monkeys = [
  { 
    items: [79, 98], 
    opp: old => old * 19, 
    test: val => val % 23 === 0,
    next: [3, 2],
    inspected: 0
  }, 
  { 
    items: [54, 65, 75, 74],
    opp: old => old + 6, 
    test: val => val % 19 === 0,
    next: [0, 2],
    inspected: 0
  }, 
  { 
    items: [79, 60, 97],
    opp: old => old * old, 
    test: val => val % 13 === 0,
    next: [3, 1],
    inspected: 0
  }, 
  { 
    items: [74],
    opp: old => old+3, 
    test: val => val % 17 === 0,
    next: [1, 0],
    inspected: 0
  }
];*/

const monkeys = [
  { 
    items: [98, 70, 75, 80, 84, 89, 55, 98],
    opp: old => old * 2, 
    test: val => val % 11 === 0,
    next: [4, 1],
    inspected: 0
  }, 
  { 
    items: [59],
    opp: old => old * old, 
    test: val => val % 19 === 0,
    next: [3, 7],
    inspected: 0
  }, 
  { 
    items: [77, 95, 54, 65, 89],
    opp: old => old + 6, 
    test: val => val % 7 === 0,
    next: [5, 0],
    inspected: 0
  }, 
  { 
    items: [71, 64, 75],
    opp: old => old + 2, 
    test: val => val % 17 === 0,
    next: [2, 6],
    inspected: 0
  }, 
  { 
    items: [74, 55, 87, 98],
    opp: old => old * 11, 
    test: val => val % 3 === 0,
    next: [7, 1],
    inspected: 0
  }, 
  { 
    items: [90, 98, 85, 52, 91, 60],
    opp: old => old + 7, 
    test: val => val % 5  === 0,
    next: [4, 0],
    inspected: 0
  }, 
  { 
    items: [99, 51],
    opp: old => old + 1, 
    test: val => val % 13 === 0,
    next: [2, 5],
    inspected: 0
  }, 
  { 
    items: [98, 94, 59, 76, 51, 65, 75],
    opp: old => old + 5, 
    test: val => val % 2 === 0,
    next: [6, 3],
    inspected: 0
  }
];

const playRound = (monkeys) => {
  monkeys.forEach((monkey, i) => {
    const itemsCopy = [...monkey.items];
    itemsCopy.forEach(item => {
      let worryLevel = monkey.opp(item);
      worryLevel = Math.floor(worryLevel / 3);
      const nextMonkey = monkey.next[+ monkey.test(worryLevel)];
      
      monkey.inspected += 1;
      monkey.items.shift();
      monkeys[nextMonkey].items.push(worryLevel);
      
      console.log(`#${i} ${item} | Worry level | ${worryLevel} to #${nextMonkey}`);
    });
  });
  
  return monkeys;
}

console.log('start');

for(let i=0; i<20; i++) {
  playRound(monkeys);
}

monkeys.sort((a,b) => b.inspected - a.inspected);

console.log(monkeys[0].inspected * monkeys[1].inspected);
```

### Part 2

```js
/*
const monkeys = [
    {
        items: [79, 98],
        opp: old => old * 19,
        base: 23,
        next: [3, 2],
        inspected: 0
    },
    {
        items: [54, 65, 75, 74],
        opp: old => old + 6,
        base: 19,
        next: [0, 2],
        inspected: 0
    },
    {
        items: [79, 60, 97],
        opp: old => old * old,
        base: 13,
        next: [3, 1],
        inspected: 0
    },
    {
        items: [74],
        opp: old => old + 3,
        base: 17,
        next: [1, 0],
        inspected: 0
    }
];*/

const monkeys = [
  {
    items: [98, 70, 75, 80, 84, 89, 55, 98],
    opp: old => old * 2,
    base: 11,
    next: [4, 1],
    inspected: 0
  },
  {
    items: [59],
    opp: old => old * old,
    base: 19,
    next: [3, 7],
    inspected: 0
  },
  {
    items: [77, 95, 54, 65, 89],
    opp: old => old + 6,
    base: 7,
    next: [5, 0],
    inspected: 0
  },
  {
    items: [71, 64, 75],
    opp: old => old + 2,
    base: 17,
    next: [2, 6],
    inspected: 0
  },
  {
    items: [74, 55, 87, 98],
    opp: old => old * 11,
    base: 3,
    next: [7, 1],
    inspected: 0
  },
  {
    items: [90, 98, 85, 52, 91, 60],
    opp: old => old + 7,
    base: 5,
    next: [4, 0],
    inspected: 0
  },
  {
    items: [99, 51],
    opp: old => old + 1,
    base: 13,
    next: [2, 5],
    inspected: 0
  },
  {
    items: [98, 94, 59, 76, 51, 65, 75],
    opp: old => old + 5,
    base: 2,
    next: [6, 3],
    inspected: 0
  }
];

const test = (val, base) => val % base === 0;

const playRound = (monkeys) => {
    const base = monkeys.reduce((acc, monkey) => acc * monkey.base, 1);

    for (const monkey of monkeys) {
        while (monkey.items.length > 0) {
            const worryLevel = monkey.opp(monkey.items.shift()) % base;
            const nextMonkey = monkey.next[+ test(worryLevel, monkey.base)];
            monkeys[nextMonkey].items.push(worryLevel);
            monkey.inspected++;
        }
    };

    return monkeys;
}

console.log('start');

for(let i=0; i<10000; i++) {
    playRound(monkeys);
}

console.log(monkeys.map(m => ({ inspected: m.inspected })));
monkeys.sort((a,b) => b.inspected - a.inspected);
console.log(monkeys[0].inspected * monkeys[1].inspected);
```
