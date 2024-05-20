
# The Gym Git Advanced Practice 

## Part 1: Refining Git History

### 1.1: Missing File Fix

```bash
Edine@DESKTOP-DTASPUT MINGW64 ~/Documents/the Gym/git Advanced Practices/gitExercises (main)
$ git status
On branch main
Your branch is based on 'origin/main', but the upstream is gone.
  (use "git branch --unset-upstream" to fixup)

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        readme.md
        test4.md

nothing added to commit but untracked files present (use "git add" to track)

Edine@DESKTOP-DTASPUT MINGW64 ~/Documents/the Gym/git Advanced Practices/gitExercises (main)
$ git add .

Edine@DESKTOP-DTASPUT MINGW64 ~/Documents/the Gym/git Advanced Practices/gitExercises (main)
$ git commit --amend
[main 2c414c8] chore: Create third and fourth files
 Date: Mon May 20 14:02:34 2024 +0200
 3 files changed, 8 insertions(+)
 create mode 100644 readme.md
 create mode 100644 test3.md
 create mode 100644 test4.md
```

### 1.2: Editing Commit History

```bash     

Edine@DESKTOP-DTASPUT MINGW64 ~/Documents/the Gym/git Advanced Practices/gitExercises (main)
$ git log
commit 49cdd08ed77de41e5bb681f1123ffe94dc2ecc0e (HEAD -> main)
Author: edine-noella <edinenoella@gmail.com>
Date:   Mon May 20 14:17:42 2024 +0200

    updated read me file

commit 2c414c88c58ba809bed8947f442ceb864ce94f6f
Author: edine-noella <edinenoella@gmail.com>
Date:   Mon May 20 14:02:34 2024 +0200

    chore: Create third and fourth files

commit 08bfafe7125acd824600c21a30fae6d867986e94
Author: edine-noella <edinenoella@gmail.com>
Date:   Mon May 20 14:02:22 2024 +0200

    chore: Create another file

commit 711e6684d286296e426990bfbf084a5ae7a92c38
Author: edine-noella <edinenoella@gmail.com>
Date:   Mon May 20 14:02:08 2024 +0200

    chore: Create initial file

Edine@DESKTOP-DTASPUT MINGW64 ~/Documents/the Gym/git Advanced Practices/gitExercises (main)
$ git rebase -i HEAD~3
[detached HEAD 94ec9eb] chore: Create second  file
 Date: Mon May 20 14:02:22 2024 +0200
 1 file changed, 0 insertions(+), 0 deletions(-)  
 create mode 100644 test2.md
Successfully rebased and updated refs/heads/main.

Edine@DESKTOP-DTASPUT MINGW64 ~/Documents/the Gym/git Advanced Practices/gitExercises (main)
$ git log
commit 08de8eca2d742a712b8c202498155694e744098f (HEAD -> main)
Author: edine-noella <edinenoella@gmail.com>
Date:   Mon May 20 14:17:42 2024 +0200

    updated read me file

commit dc50c74aaca322962572083e6ff146361e1f869b
Author: edine-noella <edinenoella@gmail.com>
Date:   Mon May 20 14:02:34 2024 +0200

    chore: Create third and fourth files

commit 94ec9eb45290ac5f3816c3fced7f05db7f86e48e
Author: edine-noella <edinenoella@gmail.com>
Date:   Mon May 20 14:02:22 2024 +0200

    chore: Create second  file

commit 711e6684d286296e426990bfbf084a5ae7a92c38
Author: edine-noella <edinenoella@gmail.com>
Date:   Mon May 20 14:02:08 2024 +0200

    chore: Create initial file

```

### 1.3: Squashing Commits

```bash
Edine@DESKTOP-DTASPUT MINGW64 ~/Documents/the Gym/git Advanced Practices/gitExercises (main)
$ git rebase -i HEAD~3
[detached HEAD be1d3cc] chore: Create initial file
 Date: Mon May 20 14:02:22 2024 +0200
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test2.md
[detached HEAD 046018d] chore: Create initial file
 Date: Mon May 20 14:02:22 2024 +0200
 4 files changed, 8 insertions(+)
 create mode 100644 readme.md
 create mode 100644 test2.md
 create mode 100644 test3.md
 create mode 100644 test4.md
Successfully rebased and updated refs/heads/main.

Edine@DESKTOP-DTASPUT MINGW64 ~/Documents/the Gym/git Advanced Practices/gitExercises (main)
$ git rebase --continue
fatal: No rebase in progress?
```

### 1.4: Splitting a Commit

```bash
Edine@DESKTOP-DTASPUT MINGW64 ~/Documents/the Gym/git Advanced Practices/gitExercises (main)
$ git rebase -i HEAD~1
Stopped at 970110d...  Create third file
You can amend the commit now, with

  git commit --amend

Once you are satisfied with your changes, run

  git rebase --continue

Edine@DESKTOP-DTASPUT MINGW64 ~/Documents/the Gym/git Advanced Practices/gitExercises (main|REBASE 1/1)
$ git reset HEAD^
Unstaged changes after reset:
M       readme.md

Edine@DESKTOP-DTASPUT MINGW64 ~/Documents/the Gym/git Advanced Practices/gitExercises (main|REBASE 1/1)
$ git add .

Edine@DESKTOP-DTASPUT MINGW64 ~/Documents/the Gym/git Advanced Practices/gitExercises (main|REBASE 1/1)
$ git commit -m "the split latest commit message"
[detached HEAD 78f8db4] the split latest commit message
 2 files changed, 10 insertions(+)
 create mode 100644 text5.md

Edine@DESKTOP-DTASPUT MINGW64 ~/Documents/the Gym/git Advanced Practices/gitExercises (main|REBASE 1/1)
$ git add .

Edine@DESKTOP-DTASPUT MINGW64 ~/Documents/the Gym/git Advanced Practices/gitExercises (main|REBASE 1/1)
$ git rebase --continue
Successfully rebased and updated refs/heads/main.

```
### 1.5: Advanced Squashing:

```bash 

Edine@DESKTOP-DTASPUT MINGW64 ~/Documents/the Gym/git Advanced Practices/gitExercises (main)
$ git rebase -i HEAD~4
[detached HEAD 5cd4dcd] Squahing two latests commits
 Date: Mon May 20 14:17:42 2024 +0200
 2 files changed, 157 insertions(+)
 create mode 100644 text5.md
Successfully rebased and updated refs/heads/main.

Edine@DESKTOP-DTASPUT MINGW64 ~/Documents/the Gym/git Advanced Practices/gitExercises (main)
$ git rebase --continue
fatal: No rebase in progress?

Edine@DESKTOP-DTASPUT MINGW64 ~/Documents/the Gym/git Advanced Practices/gitExercises (main)
$ git log
commit 5cd4dcda3440b98b72eb19db00aee835dd65fd94 (HEAD -> main)
Author: edine-noella <edinenoella@gmail.com>
Date:   Mon May 20 14:17:42 2024 +0200

    Squahing two latests commits

commit 046018df17d2f730b221338b1be77df8f2196a98
Author: edine-noella <edinenoella@gmail.com>
Date:   Mon May 20 14:02:22 2024 +0200

    chore: Create initial file

commit 711e6684d286296e426990bfbf084a5ae7a92c38
Author: edine-noella <edinenoella@gmail.com>
Date:   Mon May 20 14:02:08 2024 +0200

    chore: Create initial file
```

### 1.6: Dropping a Commit:

```bash
Edine@DESKTOP-DTASPUT MINGW64 ~/Documents/the Gym/git Advanced Practices/gitExercises (main)
$ git log
commit fa6a28582cc1aab7e5f7ad09602cdd798135207e (HEAD -> main)
Author: edine-noella <edinenoella@gmail.com>
Date:   Mon May 20 16:12:53 2024 +0200

    unwanted

commit 5cd4dcda3440b98b72eb19db00aee835dd65fd94
Author: edine-noella <edinenoella@gmail.com>
Date:   Mon May 20 14:17:42 2024 +0200

    Squahing two latests commits

commit 046018df17d2f730b221338b1be77df8f2196a98
Author: edine-noella <edinenoella@gmail.com>
Date:   Mon May 20 14:02:22 2024 +0200

    chore: Create initial file

commit 711e6684d286296e426990bfbf084a5ae7a92c38
Author: edine-noella <edinenoella@gmail.com>
Date:   Mon May 20 14:02:08 2024 +0200

    chore: Create initial file

Edine@DESKTOP-DTASPUT MINGW64 ~/Documents/the Gym/git Advanced Practices/gitExercises (main)
$ git reset --hard HEAD~1
HEAD is now at 5cd4dcd Squahing two latests commits

```
### 1.7: Reordering Commits:

```bash
git rebase -i HEAD~3
CONFLICT (modify/delete): readme.md deleted in HEAD and modified in 5cd4dcd (Squahing two latests commits).  Version 5cd4dcd (Squahing two latests commits) of readme.md left in tree.
error: could not apply 5cd4dcd... Squahing two latests commits
hint: Resolve all conflicts manually, mark them as resolved with
hint: "git add/rm <conflicted_files>", then run "git rebase --continue".
hint: You can instead skip this commit: run "git rebase --skip".
hint: To abort and get back to the state before "git rebase", run "git rebase --abort".
Could not apply 5cd4dcd... Squahing two latests commits

Edine@DESKTOP-DTASPUT MINGW64 ~/Documents/the Gym/git Advanced Practices/gitExercises (main|REBASE 1/3)
$ git add .

Edine@DESKTOP-DTASPUT MINGW64 ~/Documents/the Gym/git Advanced Practices/gitExercises (main|REBASE 1/3)
$ git rebase --continue
[detached HEAD 131e34b] Squahing two latests commits
 2 files changed, 165 insertions(+)
 create mode 100644 readme.md
 create mode 100644 text5.md
Auto-merging readme.md
CONFLICT (add/add): Merge conflict in readme.md
error: could not apply 046018d... chore: Create initial file
hint: Resolve all conflicts manually, mark them as resolved with        
hint: "git add/rm <conflicted_files>", then run "git rebase --continue".
hint: You can instead skip this commit: run "git rebase --skip".        
hint: To abort and get back to the state before "git rebase", run "git rebase --abort".
chore: Create initial file
Could not apply 046018d... chore: Create initial file

Edine@DESKTOP-DTASPUT MINGW64 ~/Documents/the Gym/git Advanced Practices/gitExercises (main|REBASE 2/3)
$ git rebase --continue
readme.md: needs merge
You must edit all merge conflicts and then
mark them as resolved using git add

Edine@DESKTOP-DTASPUT MINGW64 ~/Documents/the Gym/git Advanced Practices/gitExercises (main|REBASE 2/3)
$ git add .

Edine@DESKTOP-DTASPUT MINGW64 ~/Documents/the Gym/git Advanced Practices/gitExercises (main|REBASE 2/3)
$ git rebase --continue
[detached HEAD 9c098f0] chore: Create initial file
 3 files changed, 0 insertions(+), 0 deletions(-) 
 create mode 100644 test2.md
 create mode 100644 test3.md
 create mode 100644 test4.md
Successfully rebased and updated refs/heads/main.

Edine@DESKTOP-DTASPUT MINGW64 ~/Documents/the Gym/git Advanced Practices/gitExercises (main)
$ git add .

Edine@DESKTOP-DTASPUT MINGW64 ~/Documents/the Gym/git Advanced Practices/gitExercises (main)
$ git rebase --continue
fatal: No rebase in progress?
```

### 1.8: Cherry-Picking Commits:

```bash
Edine@DESKTOP-DTASPUT MINGW64 ~/Documents/the Gym/git Advanced Practices/gitExercises (main)
$ git checkout -b Ft/branch 
Switched to a new branch 'Ft/branch'

Edine@DESKTOP-DTASPUT MINGW64 ~/Documents/the Gym/git Advanced Practices/gitExercises (Ft/branch)
$ git add .

Edine@DESKTOP-DTASPUT MINGW64 ~/Documents/the Gym/git Advanced Practices/gitExercises (Ft/branch)
$ git commit -m "Implemented test 6"
[Ft/branch fcc0f1e] Implemented test 6
 1 file changed, 1 insertion(+)       
 create mode 100644 test6.md

Edine@DESKTOP-DTASPUT MINGW64 ~/Documents/the Gym/git Advanced Practices/gitExercises (Ft/branch)
$ git log
commit fcc0f1e233da5cafcf45f45f2e3c02c8585ebeb4 (HEAD -> Ft/branch)
commit fcc0f1e233da5cafcf45f45f2e3c02c8585ebeb4 (HEAD -> Ft/branch)
Author: edine-noella <edinenoella@gmail.com>
Date:   Mon May 20 16:38:31 2024 +0200

    Implemented test 6

commit a13db4f0cf6a1d2f015adbb9afdfc978bfe1a1e2 (origin/main, main)
Author: edine-noella <edinenoella@gmail.com>
Date:   Mon May 20 16:31:32 2024 +0200

    latests changes read me file

commit 03e53855cc86dbf2b61ffe7376d17592807749a4
Author: edine-noella <edinenoella@gmail.com>
Date:   Mon May 20 16:20:33 2024 +0200

    part 1 task 66

commit 9c098f0cdef5cd4d0e6155466a55f7dc46c63e60
Author: edine-noella <edinenoella@gmail.com>
Date:   Mon May 20 14:02:22 2024 +0200

    chore: Create initial file

commit 131e34bdb622544d396570f5b176d5455f76cf7c
Author: edine-noella <edinenoella@gmail.com>
Date:   Mon May 20 14:17:42 2024 +0200

Edine@DESKTOP-DTASPUT MINGW64 ~/Documents/the Gym/git Advanced Practices/gitExercises (Ft/branch)
$ git checkout 

Edine@DESKTOP-DTASPUT MINGW64 ~/Documents/the Gym/git Advanced Practices/gitExercises (Ft/branch)
$ git cherry-pick fcc0f1e233da5cafcf45f45f2e3c02c8585ebeb4
The previous cherry-pick is now empty, possibly due to conflict resolution.
If you wish to commit it anyway, use:

    git commit --allow-empty

Otherwise, please use 'git cherry-pick --skip'
On branch Ft/branch
You are currently cherry-picking commit fcc0f1e.
  (all conflicts fixed: run "git cherry-pick --continue")
  (use "git cherry-pick --skip" to skip this patch)
  (use "git cherry-pick --abort" to cancel the cherry-pick operation)

nothing to commit, working tree clean

Edine@DESKTOP-DTASPUT MINGW64 ~/Documents/the Gym/git Advanced Practices/gitExercises (Ft/branch|CHERRY-PICKING)
$ git checkout main
Switched to branch 'main'
warning: cancelling a cherry picking in progress
Your branch is up to date with 'origin/main'.

Edine@DESKTOP-DTASPUT MINGW64 ~/Documents/the Gym/git Advanced Practices/gitExercises (main)
$ git cherry-pick fcc0f1e233da5cafcf45f45f2e3c02c8585ebeb4
[main 3f3bab6] Implemented test 6
 Date: Mon May 20 16:38:31 2024 +0200
 1 file changed, 1 insertion(+)
 create mode 100644 test6.md
```

### 1.9: git log graph:
### 1.10: git reflog:

## Part 2: Branching Basics

### 2.1: Feature Branch Creation:

```bash
Edine@DESKTOP-DTASPUT MINGW64 ~/Documents/the Gym/git Advanced Practices/gitExercises (main)
$ git checkout -b ft/new-feature
Switched to a new branch 'ft/new-feature'
```
### 2.2: Working on the Feature Branch:

```bash
Edine@DESKTOP-DTASPUT MINGW64 ~/Documents/the Gym/git Advanced Practices/gitExercises (ft/new-feature)
$ git add .

Edine@DESKTOP-DTASPUT MINGW64 ~/Documents/the Gym/git Advanced Practices/gitExercises (ft/new-feature)
$ git commit -m "Implemented core functionality for new feature"
[ft/new-feature 743ecf5] Implemented core functionality for new feature
 2 files changed, 13 insertions(+), 1 deletion(-)
 create mode 100644 feature.txt
 ```

### 2.3 Switching Back and Making More Changes

```bash
git checkout main
Switched to branch 'main'
Your branch is up to date with 'origin/main'.

Edine@DESKTOP-DTASPUT MINGW64 ~/Documents/the Gym/git Advanced Practices/gitExercises (main)
$ git add .

Edine@DESKTOP-DTASPUT MINGW64 ~/Documents/the Gym/git Advanced Practices/gitExercises (main)
$ git commit -m "Updated project readme"
[main c996856] Updated project readme
 1 file changed, 1 deletion(-)       
 delete mode 100644 text5.md
```

### 2.4: Local vs. Remote Branches:

```bash
Edine@DESKTOP-DTASPUT MINGW64 ~/Documents/the Gym/git Advanced Practices/gitExercises (Ft/new-feature)
$ git push origin Ft/new-feature
Enumerating objects: 6, done.
Counting objects: 100% (6/6), done.
Delta compression using up to 4 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (4/4), 613 bytes | 613.00 KiB/s, done.
Total 4 (delta 2), reused 0 (delta 0), pack-reused 0        
remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
remote:
remote: Create a pull request for 'Ft/new-feature' on GitHub by visiting:
remote:      https://github.com/edine-noella/gitExercises/pull/new/Ft/new-feature
remote:
To https://github.com/edine-noella/gitExercises.git  
 * [new branch]      Ft/new-feature -> Ft/new-feature

Edine@DESKTOP-DTASPUT MINGW64 ~/Documents/the Gym/git Advanced Practices/gitExercises (Ft/new-feature)
$ git checkout main
Switched to branch 'main'
Your branch is ahead of 'origin/main' by 2 commits.
  (use "git push" to publish your local commits)

Edine@DESKTOP-DTASPUT MINGW64 ~/Documents/the Gym/git Advanced Practices/gitExercises (main)
$ git pull
remote: Enumerating objects: 1, done.
Unpacking objects: 100% (1/1), 925 bytes | 154.00 KiB/s, done.100% (1/1)

remote: Total 1 (delta 0), reused 0 (delta 0), pack-reused 0
From https://github.com/edine-noella/gitExercises
   62f9096..be56651  main       -> origin/main
Auto-merging readme.md
CONFLICT (content): Merge conflict in readme.md
Automatic merge failed; fix conflicts and then commit the result.
```

### 2.5: Branch Deletion:

```bash
Edine@DESKTOP-DTASPUT MINGW64 ~/Documents/the Gym/git Advanced Practices/gitExercises (main)
$ git branch
  Ft/branch
  Ft/new-feature
* main

Edine@DESKTOP-DTASPUT MINGW64 ~/Documents/the Gym/git Advanced Practices/gitExercises (main)
$ git branch -d Ft/new-feature
Deleted branch Ft/new-feature (was 0078708).
```
### 2.6: Creating a Branch from a Commit
```bash
Edine@DESKTOP-DTASPUT MINGW64 ~/Documents/the Gym/git Advanced Practices/gitExercises (main)
$ git checkout -b ft/new-branch-from-commit a5d15c8dac5459440ea1f3d26bae3d4a7b4577f0
Switched to a new branch 'ft/new-branch-from-commit'
```
### 2.7: branch Merging
```bash
