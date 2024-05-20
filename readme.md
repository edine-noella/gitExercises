
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
