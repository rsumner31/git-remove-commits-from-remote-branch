# git-remove-commits-from-remote-branch

### 1 Revert the full commit

```sh
$ git revert dd61ab23
```

### 2 Delete the last commit

```sh
$ git push <<remote>> +dd61ab23^:master
```

or, if the branch is available locally

```sh
$ git reset HEAD^ --hard
$ git push <<remote>> -f
```

where +dd61... is your commit hash and git interprets x^ as the parent of x, and + as a forced non-fastforwared push.

### 3 Delete the commit from a list

```sh
$ git rebase -i dd61ab23^
```

This will open and editor showing a list of all commits. Delete the one you want to get rid off. Finish the rebase and push force to repo.

```sh
$ git rebase --continue
$ git push <remote_repo> <remote_branch> -f
or
$ $git push origin +master
```

Notice the + sign before the name of the branch you are pushing, this tells git to force the push.
