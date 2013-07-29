Usually when you run a command you get an exit status of `0`. So instead of checking the result of a command with a regex you can check the exit status.
```
`ping -q -c #{ping_count} #{server}`
if $?.exitstatus == 0
    # do something
end
```
