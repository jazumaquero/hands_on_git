# Managing working areas

## Before start
This guide will be organized mainly as a set of exercises that will require running some very easy scripts on bash (I recommend using _GitBash_ or _WSL2_ if you are working on a _Windows_ machine)

## What is tracked by git?
Easy way of finding out what is being tracked or not is using the status command
```bash
git status
```

Remember that `Git` tracks files, not directories. This is mainly due to commit structure, that are storing file changes.
So that, if you have an empty directory, it will never appear on the repository area.

To verify this, just let's create some empty file and some empty directory:
```bash
touch some_empty_file.txt
mkdir -p some_empty_directory
```

And now verify what appear when checking the status
```bash
git status
```

Then you will see something like following:
```shell
On branch master                                                
                                                                
No commits yet                                                  
                                                                
Untracked files:                                                
  (use "git add <file>..." to include in what will be committed)
        some_empty_file.txt

nothing added to commit but untracked files present (use "git add" to track)
```

## How can indicate I want to include my changes on next commit?
As you can see, we have just added a file to our _working directory_, but this file is not tracked, so that, we cannot still commit this changes.
To add this changes you can just run
```bash
git add -A
git status
```

This will return following:
```bash
$ git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   some_empty_file.txt
```

Now, `some_emtpy_file.txt` has been added to the staging area, and current changes will be included on next commit.

## Wait, I forgot to add something!
Lets see what is happening if you add change to `some_emtpy_file.txt`
```bash
echo "Dude, where's my car?" >> some_empty_file.txt
```

You will obtain something like following:
```shell
$ git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   some_empty_file.txt

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   some_empty_file.txt


```
😨 Wait! what the hell has happened here?
Now I can see that `some_emtpy_file.txt` is included on the list of changes will be commited,...but it is also included on the list of changes that has not be staged for commit.
Don't worry. What has happened is that all new changes introduced after `git add` are not included on the _staging area_ yet, and they are still on the _working area_.
You can easily verify what is on staging area and what is not just using `git diff` command

If you run following command you will see only changes that are on staging area
```bash
git diff --cached
```
It will return what is on the staging area
```shell
diff --git a/some_empty_file.txt b/some_empty_file.txt
new file mode 100644
index 0000000..e69de29
```

On the other hand, following command will show you all changes on working directory
```bash
git diff --cached
```
It will return following
```shell
warning: in the working copy of 'some_empty_file.txt', LF will be replaced by CRLF the next time Git touches it
diff --git a/some_empty_file.txt b/some_empty_file.txt
index e69de29..14e6db2 100644
--- a/some_empty_file.txt
+++ b/some_empty_file.txt
@@ -0,0 +1 @@
+Dude, where's my car?
```

## Finish it!
Once you have added all changes, you can commit them with `commit` command:
```bash
git add -A
git commit -m "Dude, where's my car?"
```

After commiting your changes, all changes tracked on _staging area_ will be moved to _repository area_, so that, running status will return something like following
```shell
$ git status                                                         
On branch master
nothing to commit, working tree clean
```

Furthermore, you can verify that you commit is now appearing on the history (just on local), that can be retrieve using `log`command:
```shell
$ git log
commit 65921038bc9db7f6ddeacbe73ed8d3d4da4a95fb (HEAD -> master)
Author: Jose Antonio Zumaquero Torres <jazumaquero@gmail.com>
Date:   Mon Jan 8 16:33:45 2024 +0100

    Dude, where's my car?

commit e7ea9b7961891df8e184f4868ad0494257e5d98e
Author: Jose Antonio Zumaquero Torres <jazumaquero@gmail.com>
Date:   Mon Jan 8 16:17:21 2024 +0100

    init

```

Rember that `log` command is some amazing tool, including a lot of arguments, that allows showing history with amazing formats, for instance:
```shell
$ git log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit
* 6592103 - (HEAD -> master) Dude, where's my car? (2 minutes ago) <Jose Antonio Zumaquero Torres>
* e7ea9b7 - init (19 minutes ago) <Jose Antonio Zumaquero Torres>

```

## Summary
On this tutorial you should have learnt following:

* How to find out what is on each of the 3 git areas (working, staging, repository) using `status` command.
* How to add changes using `add` command.
* How to see commit history using `log` command.
