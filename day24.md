# Challenge #24: The last challenge is a maze

### Cognitive Complexity: 36 (> 1000 ops/s)

```js
function canExit(maze) {
  const getStartAndEndPos = (input) => {
    let startPos = [0,0];
    let endPos = [0,0];

    for (let i=0; i<input.length; i++) {
        for (let j=0; j < input[i].length; j++) {
            if (input[i][j] === 'S') {
                startPos = [i, j];
            } else if (input[i][j] === 'E') {
                endPos = [i, j];
            }
        }
    }

    return { startPos, endPos };
  }

  const getValidAdjacents = (heightsMap, currPos) => {  
      const [row, col] = currPos;
      const currHeight = heightsMap[row][col];
      const adjacent = [];
      const validStep = [' ', 'E'];

      const right = heightsMap[row].length>col+1 && 
            validStep.includes(heightsMap[row][col+1]);
      const left = col-1 >= 0 && 
            validStep.includes(heightsMap[row][col-1]);
      const down = heightsMap.length>row+1 && 
            validStep.includes(heightsMap[row+1][col]);
      const up = row-1 >= 0 && 
            validStep.includes(heightsMap[row-1][col]);

      if (right) {
        adjacent.push([row, col+1]);
      }
      if (left) {
        adjacent.push([row, col-1]);
      }
      if (down) {
        adjacent.push([row+1, col]);
      }
      if (up) {
        adjacent.push([row-1, col]);
      }

      return adjacent;
  }

  const breadthFirstSearch = (heightsMap, startPos, endFunction) => {
      const queue = [];
      const visited = new Set();
      const steps = new Map();

      // Initialize all with start position
      queue.push(startPos);
      steps.set(startPos.toString(), 0);
      visited.add(startPos.toString());

      while(queue.length > 0) {
          const currPos = queue.shift();
          const currPosKey = currPos.toString();

          if (endFunction(currPos)) {
            return steps.get(currPosKey);
          }

          const neighbours = getValidAdjacents(heightsMap, currPos);
          for (const adjacent of neighbours) {
              const adjacentPosKey = adjacent.toString();
              const adjacentVisited = visited.has(adjacentPosKey);
              const numberOfStepsIsShorter = 
                    steps.get(currPosKey)+1 < steps.get(adjacentPosKey);

              if (!adjacentVisited || numberOfStepsIsShorter) {
                  steps.set(adjacentPosKey, steps.get(currPosKey)+1);
                  queue.push(adjacent);
                  visited.add(adjacentPosKey);
              }
          }

          //console.log('Queue:', queue);
          //console.log('Visited:', JSON.stringify(Array.from(visited)));
          //console.log('Steps:', [...steps.entries()]);
      }
  }
  
  const { startPos, endPos } = getStartAndEndPos(maze);
  return !!breadthFirstSearch(maze, startPos, 
           (currPos) => currPos[0] === endPos[0] && currPos[1] === endPos[1]);
}
```
