git checkout
git branch

# "master"

Hier oder in github?
add / remove
fetch push pull (https://www.youtube.com/watch?v=xdao5LCNoYE&index=15&list=PLg7s6cbtAD15G8lNyoaYDuKZSKyJrgwB-)

## merge vs. rebase
➪ Only rebase commits that exist in your local repository.

Da Dezentral: Jeder Entwickler hat eigenen branch


# Weiteres

### Move the last commit to a new branch
```bash
# create new branch from
# current HEAD
# but stays on master
$ git branch <new-branch-name>

# reset master to before last commit
$ git reset --hard HEAD~

# continue on new branch
$ git checkout <new-branch-name>
```
