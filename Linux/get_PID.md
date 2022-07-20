# Use command to get pid on ubuntu

```
# change "command" as the command you want to get
ps -ef | grep "command" | grep -v grep | cut -c 9-15 
```
