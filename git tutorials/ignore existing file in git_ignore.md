### when you have a file in remote repository and now you want to ignore this file by git ignore but it's not working ( not ignoring ) then Try This

1. push all of update if have any
2. 
```
git rm -r --cached .
```

3.add , commit -m "git ignore working now" , push again
