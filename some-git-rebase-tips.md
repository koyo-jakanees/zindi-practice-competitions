Login as default user: sudo -i -u postgres
Create new User: createuser --interactive
When prompted for role name, enter linux username, and select Yes to superuser question.
 Still logged in as postgres user, create a database: createdb <username_from_step_3>
Confirm error(s) are gone by entering: psql at the command prompt.
Output should show psql (x.x.x) Type "help" for help.
[gitbook](https://git-scm.com/book/en/v2/Git-Branching-Rebasing)
[atlassian](https://www.atlassian.com/git/tutorials/rewriting-history/git-rebase)
[gist](https://gist.github.com/ravibhure/a7e0918ff4937c9ea1c456698dcd58aa)
[algolia](https://blog.algolia.com/master-git-rebase/)
[w3doc](https://www.w3docs.com/snippets/git/how-to-rebase-git-branch.html)
shorthand when in another branch
```sh
git pull --rebase master
```
```sh
git pull --continue
```

Fetching changes¶

- You should receive the latest changes from a remote git repository. Thus the first step is running git fetch:
 ```sh
git fetch
```

- Integrating changes¶

The second step is running git rebase. Rebase is a Git command which is used to integrate changes from one branch into another. The following command rebase the current branch from master (or choose any other branch like develop, suppose, the name of remote is origin, which is by default):
```sh
git rebase origin/master
```

After git rebase, conflicts may occur. You should resolve them and add your changes by running git add command:
```sh
git add .
```

Do not run git commit after ```sh git add .```
After resolving the conflicts and adding the changes to the staging area, you must run git rebase with the --continue option:
```git rebase --continue```

If you want to cancel the rebasing rather than resolving the conflicts, you can run the following:

```git rebase --abort```

Pushing changes¶

The final step is git push (forced). This command uploads local repository content to a remote repository. To do that, run the command below:

```git push origin HEAD -f```


--force that is the same as -f overwrites the remote branch on the basis of your local branch. It destroys all the pushed changes made by other developers. It refers to the changes that you don't have in your local branch.
Here is an alternative and safer way to push your changes:

```sh
git push --force-with-lease origin HEAD
```

```--force-with-lease``` is considered a safer option that will not overwrite the work done on the remote branch in case more commits were attached to it (for instance, by another developer). Moreover, it helps you to avoid overwriting another developer's work by force pushing.




- Rebasing vs Merging¶

Rebasing and merging are both used to integrate changes from one branch into another differently. They are both used in different scenarios. If you need to update a feature branch, always choose to rebase for maintaining the branch history clean. It keeps the commit history out of the branch, contrary to the git merge command, which is its alternative. While, for individuals, rebasing is not recommended in the case of feature branch because when you share it with other developers, the process may create conflicting repositories. Once you need to put the branch changes into master, use merging. If you use merging too liberally, it will mess up git log and make difficult to understand the history. Merging preserves history whereas rebasing rewrites it. If you need to see the history absolutely the same as it happened, then use merge.
Fetching¶

The git fetch command downloads commits, files, and refs from a remote repository into the local repository. It updates your remote-tracking branches. The git fetch command allows you to see the progress of the central history, not forcing you to merge the changes into your repository. It does not affect your local work process.
