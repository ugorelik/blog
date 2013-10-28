How to delete merged branches in git

``` bash
git br --merged | grep -v \* | grep -v master | xargs git br -d
```

You can also create a git alias:

``` bash
git config --global alias.dm \
'!sh -c "git br --merged | grep -v \* | grep -v master | xargs git br -d"'
```
