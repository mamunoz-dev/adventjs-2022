# Challenge #23: Santa Claus Compiler

### Cognitive Complexity: 4 (>1000 ops/sec)

```js
function executeCommands(commands) {
  const regs = new Array(8).fill(0);
  const getRegIndex = (arg) => Number(arg.at(-1));
  const mod = (n, m) => ((n % m) + m) % m;
  const execute = (commands) => {
    commands.forEach((c, i) => {
      const [cmd, args] = c.split(' ');
      commandFns[cmd](args, commands, i);
    });
  };
 
  const commandFns = {
    'MOV': (args) => {
      args = args.split(',');
      regs[getRegIndex(args[1])] = 
        args[0].charAt(0) === 'V' ? 
          regs[getRegIndex(args[0])] : Number(args[0]);
     },
    'ADD': (args) => {
      args = args.split(',');
      regs[getRegIndex(args[0])] = 
        mod(regs[getRegIndex(args[0])] + regs[getRegIndex(args[1])], 256);
     },
    'DEC': (args) => {
      regs[getRegIndex(args)] = mod(regs[getRegIndex(args)] - 1, 256);
    },
    'INC': (args) => {
      regs[getRegIndex(args)] = mod(regs[getRegIndex(args)] + 1, 256)
    },
    'JMP': (args, commands, i) => {
      while(regs[0] !== 0) {
        execute(commands.slice(Number(args), i));
      }
    }
  };
  
  execute(commands);
  
  return regs;      
}
```
