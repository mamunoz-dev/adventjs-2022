# Challenge #20: More challenging trips

### Cognitive Complexity: 3 (~500 ops/s)

```js
function howManyReindeers(reindeerTypes, gifts) {
  const reindeerCapacities = reindeerTypes
    .sort((a, b) => b.weightCapacity - a.weightCapacity)
    .map(elm => elm.weightCapacity);
  const countriesWeights = gifts.map(elm => elm.weight);
  
  const countryDistributions = countriesWeights.reduce((acc, weight) => {
    const reindeerDistribution = 
          Array.from(new Array(reindeerTypes.length)).fill(0);

    while(weight > 0) {
      const reindeerIndex = reindeerCapacities
      .findIndex((curr, i) => 
                 curr <= weight && 
                 reindeerDistribution
                   .slice(i+1)
                   .every(elm => elm >= reindeerDistribution[i]+1));
      reindeerDistribution[reindeerIndex]++;
      weight -= reindeerCapacities[reindeerIndex];
    }
    
    acc.push(reindeerDistribution);
    
    return acc;
  }, []);
  
  return gifts.map((gift, i) => {
    const reindeers = countryDistributions[i]
      .map((num, j) => ({ type: reindeerTypes[j].type, num }))
      .filter(elm => elm.num > 0);
    
    return { 
      country: gift.country, 
      reindeers
    };
  });
}
```
