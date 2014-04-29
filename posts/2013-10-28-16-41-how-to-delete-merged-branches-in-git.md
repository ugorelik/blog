How to delete merged branches in git

``` bash
git branch --merged | grep -v \* | grep -v master | xargs git branch -d
```

You can also create a git alias:

``` bash
git config --global alias.dm \
'!sh -c "git branch --merged | grep -v \* | grep -v master | xargs git branch -d"'
```
