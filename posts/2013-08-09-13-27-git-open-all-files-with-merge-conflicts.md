``` bash
git diff --name-only | uniq | xargs subl
```

I found it useful to create an alias too:

``` bash
git config --global alias.mc \
'!sh -c "git diff --name-only | uniq | xargs subl"'
```

And of course you can substitute subl for your favorite editor.
