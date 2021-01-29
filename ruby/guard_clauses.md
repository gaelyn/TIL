# Guard Clause

A guard clause is a line of code that guard the rest of the code against certain criteria
Example from `/ruby-exercises/mythical-creatures/medusa.rb` :
```
def stare(victim)
  return false if statues.count >= 3

  statues << victim
  victim.make_stoned
end
```

The line `return false if statues.count >= 3` will escape you out of the method if there is 3 or more statues in the statue array.

In other words, it guards the rest of the code against the condition that there can't be
more than 3 statues in the array. 
