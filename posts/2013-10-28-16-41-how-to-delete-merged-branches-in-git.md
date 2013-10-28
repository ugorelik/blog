How to delete merged branches in git

```
git br --merged | grep -v \* | grep -v master | xargs git br -d
```

You can also create a git alias:

```
git config --global alias.dm \
'!sh -c "git br --merged | grep -v \* | grep -v master | xargs git br -d"'
```
