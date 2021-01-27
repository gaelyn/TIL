# How to add an alias
Desired results: when I type "til" 2 things happen
1. `cd` into `/Users/gjc/my_stuff/til`
2. Run `atom .` command
1. open up `.zshrc` in atom: `atom ~.zshrc`
2. add the following : `alias til="cd /Users/gjc/my_stuff/til && atom ."`
2. type `source ~/.zshrc` into terminal

## Aliases

```
alias til="cd /Users/gjc/my_stuff/til && atom ."

alias ls="ls -lahGgo"
```
