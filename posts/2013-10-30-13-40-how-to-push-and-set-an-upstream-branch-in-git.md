I like to use [hub](http://hub.github.com/), and mainly for creating pull requests in the console. To do so you have push and set an upstream branch: `git push -u origin CURRENT_BRANCH_NAME`. I found myself calling the remote branch the same as my local branch which became tedious so I created a shortcut: `git pu`.


##### Basic command
``` bash
git rev-parse --abbrev-ref HEAD | xargs git push -u origin
```

##### Git alias

``` bash
git config --global alias.pu \
'!sh -c "git rev-parse --abbrev-ref HEAD | xargs git push -u origin"'
```
