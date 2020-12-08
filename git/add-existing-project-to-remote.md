# Adding an existing project to a remote repository
Often you'll have started working on a prototype and then want to add it to a remote version control repository. First you'll need to create a local repo:
```
git init
git add .
git commit -m "first commit"
```
Next: `git remote add origin` and add the url of your git repository:
```
git remote add origin https://TriasDev@dev.azure.com/TriasDev/Routing%20Test/_git/Routing%20Test
```

And now to push the changes to origin:
```
git remote -v
git push origin master
```