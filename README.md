# GIT Exercises

## Bundle 1

### Exercise 1

- Question 1:

  1. Create a project & initialize git

  ```
  😹 🍒 :git-exercises ivy$ git init
  Initialized empty Git repository in /home/ivy/ojemba/git-exercises/.git/
  ```

  2. Rename your main branch from master to main

  ```
  😹 🍒 :git-exercises ivy$ git branch -m main

  ```

  3. Make changes to the project (add files, rename them or edit them)

  ```
  😹 🍒 :git-exercises ivy$ touch index.html
  😹 🍒 :git-exercises ivy$ git status
  On branch main

  No commits yet

  Untracked files:
  (use "git add <file>..." to include in what will be committed)
      index.html

  nothing added to commit but untracked files present (use "git add" to track)
  ```

  4. Stage your changes and commit them

  ```
  😹 🍒 :git-exercises ivy$ git add index.html
  😹 🍒 :git-exercises ivy$ git commit -m 'Add index file'
  [main (root-commit) cf80077] Add index file
  1 file changed, 0 insertions(+), 0 deletions(-)
  create mode 100644 index.html
  ```

  5. Create a github repo and connect it with your project

  ```
  😹 🍒 :git-exercises ivy$ git remote add origin git@github.com:IvyMurage/git-exercises.git
  😹 🍒 :git-exercises ivy$ git remote
  origin
  😹 🍒 :git-exercises ivy$ git remote -v
  origin	git@github.com:IvyMurage/git-exercises.git (fetch)
  origin	git@github.com:IvyMurage/git-exercises.git (push)
  ```

  6. Push your changes to github

  ```
  😹 🍒 :git-exercises ivy$     git push --set-upstream origin main
  Enumerating objects: 3, done.
  Counting objects: 100% (3/3), done.
  Writing objects: 100% (3/3), 220 bytes | 220.00 KiB/s, done.
  Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
  To github.com:IvyMurage/git-exercises.git
  * [new branch]      main -> main
  Branch 'main' set up to track remote branch 'main' from 'origin'.
  ```

  7. Create a new branch dev

  ```
  😹 🍒 :git-exercises ivy$ git checkout -b dev
  Switched to a new branch 'dev'
  😹 🍒 :git-exercises ivy$ git branch
  * dev
  main
  ```

  8. From dev create another branch test

  ```
  😹 🍒 :git-exercises ivy$ git switch -c test
  Switched to a new branch 'test'
  ```

  9. Go back to the dev branch and delete the test branch

  ```
  😹 🍒 :git-exercises ivy$ git switch dev
  Switched to branch 'dev'
  😹 🍒 :git-exercises ivy$ git branch
  * dev
  main
  test

  😹 🍒 :git-exercises ivy$ git branch -d test
  Deleted branch test (was cf80077).
  😹 🍒 :git-exercises ivy$ git branch
  * dev
  main
  ```

### Exercise 2

- Question 1:

  - Create a new home.html file, add some html changes and save them

  ```
  😹 🍒 :git-exercises ivy$ touch home.html
  😹 🍒 :git-exercises ivy$ git status
  On branch dev
  Untracked files:
  (use "git add <file>..." to include in what will be committed)
      home.html

  nothing added to commit but untracked files present (use "git add" to track)
  ```

  - Stash save your current changes

  ```
  😹 🍒 :git-exercises ivy$ git add .
  😹 🍒 :git-exercises ivy$ git status
  On branch dev
  Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
      new file:   home.html

  😹 🍒 :git-exercises ivy$ git stash
  Saved working directory and index state WIP on dev: cf80077 Add index file
  😹 🍒 :git-exercises ivy$ git status
  On branch dev
  nothing to commit, working tree clean
  😹 🍒 :git-exercises ivy$ git stash list
  stash@{0}: WIP on dev: cf80077 Add index file
  ```

  - Repeat the same process for a new about page and stash save your changes

  ```
  😹 🍒 :git-exercises ivy$ touch about.html
  😹 🍒 :git-exercises ivy$ git status
  On branch dev
  Untracked files:
  (use "git add <file>..." to include in what will be committed)
      about.html

  nothing added to commit but untracked files present (use "git add" to track)
  😹 🍒 :git-exercises ivy$ git add .
  😹 🍒 :git-exercises ivy$ git stash save ' this is the about page'
  Saved working directory and index state On dev:  this is the about page
  😹 🍒 :git-exercises ivy$ git stash list
  stash@{0}: On dev: this is the about page
  stash@{1}: WIP on dev: cf80077 Add index file
  ```

  - Repeat the same process for a new team page and stash save your changes

  ```
  😹 🍒 :git-exercises ivy$ touch team.html
  😹 🍒 :git-exercises ivy$ git status
  On branch dev
  Untracked files:
  (use "git add <file>..." to include in what will be committed)
      team.html

  nothing added to commit but untracked files present (use "git add" to track)
  😹 🍒 :git-exercises ivy$ git add .
  😹 🍒 :git-exercises ivy$ git stash save 'this is the team page'
  Saved working directory and index state On dev: this is the team page
  😹 🍒 :git-exercises ivy$ git stash list
  stash@{0}: On dev: this is the team page
  stash@{1}: On dev: this is the about page
  stash@{2}: WIP on dev: cf80077 Add index file
  ```

  - Using stash pop restore the changes of the about page

  ```
  😹 🍒 :git-exercises ivy$ git stash pop stash@{1}
  On branch dev
  Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
      new file:   about.html

  Dropped stash@{1} (d6da42affab2d0ed4fa1228718de644f445ff59c)
  😹 🍒 :git-exercises ivy$ git stash list
  stash@{0}: On dev: this is the team page
  stash@{1}: WIP on dev: cf80077 Add index file
  ```

  - With the help of an index use stash pop bring back the home page changes

  ```
  😹 🍒 :git-exercises ivy$ git stash pop 1
  On branch dev
  Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
      new file:   about.html
      new file:   home.html

  Dropped refs/stash@{1} (f45c6f3ab707a41843045e3ebec1f49c2313c84c)
  ```

  - Commit the current changes and push them

  ```
  git commit -m 'Add home and about page'
  [dev 206df2b] Add home and about page
  2 files changed, 25 insertions(+)
  create mode 100644 about.html
  create mode 100644 home.html
  ```

  - Using stash pop restore the changes of the team page index

  ```
  😹 🍒 :git-exercises ivy$ git stash list
  stash@{0}: On dev: this is the team page
  😹 🍒 :git-exercises ivy$ git stash apply
  On branch dev
  Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
      new file:   team.html

  😹 🍒 :git-exercises ivy$ git stash list
  stash@{0}: On dev: this is the team page
  😹 🍒 :git-exercises ivy$ git stash pop
  On branch dev
  Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
      new file:   team.html

  Dropped refs/stash@{0} (217b6e079ebec4486d4d7bdf6e01b0ac6f6d41ce)
  😹 🍒 :git-exercises ivy$ git stash list
  ```

  - Reset the current changes using git reset and go back to the changes without the team page

  ```
  😹 🍒 :git-exercises ivy$ git status
  On branch dev
  Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
      new file:   team.html

  😹 🍒 :git-exercises ivy$ git reset --hard
  HEAD is now at 206df2b Add home and about page
  😹 🍒 :git-exercises ivy$ git status
  On branch dev
  nothing to commit, working tree clean
  ```

## Bundle 2

### Exercise 1

- Question 1:

  - Create a new branch named ft/bundle-2:

  ```
  😹 🍒 :git-exercises ivy$ git switch -c ft/bundle-2
  Switched to a new branch 'ft/bundle-2'
  😹 🍒 :git-exercises ivy$ git branch
  dev
  * ft/bundle-2
  main
  ```

  - Add new changes to your project. create a new page named services.html and add some changes

  ```
  😹 🍒 :git-exercises ivy$ touch services.html
  😹 🍒 :git-exercises ivy$ code .
  😹 🍒 :git-exercises ivy$ git status
  On branch ft/bundle-2
  Untracked files:
  (use "git add <file>..." to include in what will be committed)
      services.html

  nothing added to commit but untracked files present (use "git add" to track)
  ```

  - Commit your changes and create a Pull Request against the main branch in your github repository

  ```
  😹 🍒 :git-exercises ivy$ git add .
  😹 🍒 :git-exercises ivy$ git commit -m 'Set the service page'
  [ft/bundle-2 b9401b4] Set the service page
  1 file changed, 14 insertions(+)
  create mode 100644 services.html

  😹 🍒 :git-exercises ivy$     git push --set-upstream origin ft/bundle-2
  Enumerating objects: 8, done.
  Counting objects: 100% (8/8), done.
  Delta compression using up to 8 threads
  Compressing objects: 100% (7/7), done.
  Writing objects: 100% (7/7), 833 bytes | 416.00 KiB/s, done.
  Total 7 (delta 3), reused 0 (delta 0), pack-reused 0
  remote: Resolving deltas: 100% (3/3), done.
  remote:
  remote: Create a pull request for 'ft/bundle-2' on GitHub by visiting:
  remote:      https://github.com/IvyMurage/git-exercises/pull/new/ft/bundle-2
  remote:
  To github.com:IvyMurage/git-exercises.git
  * [new branch]      ft/bundle-2 -> ft/bundle-2
  Branch 'ft/bundle-2' set up to track remote branch 'ft/bundle-2' from 'origin'.
  ```

  - Request a review and make sure your Pull request gets merged (Look for someone to merge your PR)

  ![plot](/images/Screenshot%20from%202024-04-22%2013-32-45.png)

### Exercise 2

- Question 1:

  - Checkout your main branch and pull the latest changes

  ```
  😹 🍒 :git-exercises ivy$ git branch
  dev
  * ft/bundle-2
  main
  😹 🍒 :git-exercises ivy$ git switch main
  Switched to branch 'main'
  Your branch is up to date with 'origin/main'.
  😹 🍒 :git-exercises ivy$ git pull
  remote: Enumerating objects: 1, done.
  remote: Counting objects: 100% (1/1), done.
  remote: Total 1 (delta 0), reused 0 (delta 0), pack-reused 0
  Unpacking objects: 100% (1/1), 896 bytes | 896.00 KiB/s, done.
  From github.com:IvyMurage/git-exercises
  cf80077..3c8cc40  main       -> origin/main
  Updating cf80077..3c8cc40
  Fast-forward
  about.html    | 11 +++++++++++
  home.html     | 14 ++++++++++++++
  services.html | 14 ++++++++++++++
  3 files changed, 39 insertions(+)
  create mode 100644 about.html
  create mode 100644 home.html
  create mode 100644 services.html
  ```

  - Create a new branch named ft/service-redesign

  ```
  😹 🍒 :git-exercises ivy$ git switch -c ft/service-redesign
  Switched to a new branch 'ft/service-redesign'
  ```

  - Add new changes to the service.html page

  ```
  😹 🍒 :git-exercises ivy$ git status
  On branch ft/service-redesign
  Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
      modified:   services.html

  no changes added to commit (use "git add" and/or "git commit -a")
  ```

  - commit and push them

  ```
  😹 🍒 :git-exercises ivy$ git add .
  😹 🍒 :git-exercises ivy$ git status
  On branch ft/service-redesign
  Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
      modified:   services.html

  😹 🍒 :git-exercises ivy$ git commit -m 'Create a header for service page'
  [ft/service-redesign a392372] Create a header for service page
  1 file changed, 2 insertions(+)
  😹 🍒 :git-exercises ivy$ git push
  fatal: The current branch ft/service-redesign has no upstream branch.
  To push the current branch and set the remote as upstream, use

      git push --set-upstream origin ft/service-redesign

  😹 🍒 :git-exercises ivy$ git push --set-upstream origin ft/service-redesign
  Enumerating objects: 5, done.
  Counting objects: 100% (5/5), done.
  Delta compression using up to 8 threads
  Compressing objects: 100% (3/3), done.
  Writing objects: 100% (3/3), 336 bytes | 336.00 KiB/s, done.
  Total 3 (delta 2), reused 0 (delta 0), pack-reused 0
  remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
  remote:
  remote: Create a pull request for 'ft/service-redesign' on GitHub by visiting:
  remote:      https://github.com/IvyMurage/git-exercises/pull/new/ft/service-redesign
  remote:
  To github.com:IvyMurage/git-exercises.git
  * [new branch]      ft/service-redesign -> ft/service-redesign
  Branch 'ft/service-redesign' set up to track remote branch 'ft/service-redesign' from 'origin'.
  ```

  - create a new PR for your changes

  - go back to your main branch and add again new changes to your service.html page, you can add different changes but make sure to affect the same part(line of code) as you did in the other PR

  ```
  😹 🍒 :git-exercises ivy$ git switch main
  Switched to branch 'main'
  Your branch is up to date with 'origin/main'.
  😹 🍒 :git-exercises ivy$ git status
  On branch main
  Your branch is up to date with 'origin/main'.

  Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
      modified:   services.html

  no changes added to commit (use "git add" and/or "git commit -a")
  😹 🍒 :git-exercises ivy$ git branch
  dev
  ft/bundle-2
  ft/service-redesign
  * main
  ```

  - Commit and push those changes

  ```
  😹 🍒 :git-exercises ivy$ git add .
  😹 🍒 :git-exercises ivy$ git commit -m 'Update service page'
  [main 0a164e5] Update service page
  1 file changed, 7 insertions(+)
  😹 🍒 :git-exercises ivy$ git push
  Enumerating objects: 5, done.
  Counting objects: 100% (5/5), done.
  Delta compression using up to 8 threads
  Compressing objects: 100% (3/3), done.
  Writing objects: 100% (3/3), 496 bytes | 496.00 KiB/s, done.
  Total 3 (delta 1), reused 0 (delta 0), pack-reused 0
  remote: Resolving deltas: 100% (1/1), completed with 1 local object.
  To github.com:IvyMurage/git-exercises.git
  3c8cc40..0a164e5  main -> main
  ```

  - n your project checkout the ft/service-redesignbranch

  ```
  😹 🍒 :git-exercises ivy$ git merge ft/service-redesign
  Auto-merging services.html
  CONFLICT (content): Merge conflict in services.html
  Automatic merge failed; fix conflicts and then commit the result.
  ```

  - Compare the ft/service-redesignwith the main branch using git diff and observe the changes

  ```
  😹 🍒 :git-exercises ivy$ git diff
  diff --cc services.html
  index 85366c6,274003a..0000000
  --- a/services.html
  +++ b/services.html
  @@@ -8,7 -8,7 +8,11 @@@
  </head>

  <body>
  ++<<<<<<< HEAD
  +    <h1>Services Page for our company 12345</h1>
  ++=======
  +     <h1>Services Page for our company</h1>
  ++>>>>>>> ft/service-redesign
      <p>This is the service page</p>
  </body>
  ```

  - Using git merge, merge the main branch with ft/service-redesign branch and commit and push you changes again

  ```
  😹 🍒 :git-exercises ivy$ git status
  On branch main
  Your branch is up to date with 'origin/main'.

  All conflicts fixed but you are still merging.
  (use "git commit" to conclude merge)

  Changes to be committed:
      modified:   services.html

  😹 🍒 :git-exercises ivy$ git diff
  😹 🍒 :git-exercises ivy$ git add .
  😹 🍒 :git-exercises ivy$ git commit -m 'resolve conflict'
  [main e107ad6] resolve conflict
  😹 🍒 :git-exercises ivy$ git push
  Enumerating objects: 1, done.
  Counting objects: 100% (1/1), done.
  Writing objects: 100% (1/1), 223 bytes | 223.00 KiB/s, done.
  Total 1 (delta 0), reused 0 (delta 0), pack-reused 0
  To github.com:IvyMurage/git-exercises.git
  270df24..e107ad6  main -> main
  ```

## Bundle 3

### Exercise 1

- Question 1:

  - Create a new branch named ft/team-page

  ```
  😹 🍒 :git-exercises ivy$ git switch -c ft/team-page
  Switched to a new branch 'ft/team-page'
  ```

  - Create a new html page named team.html and add some changes

  ```
  😹 🍒 :git-exercises ivy$ touch team.html
  😹 🍒 :git-exercises ivy$ git status
  On branch ft/team-page
  Untracked files:
  (use "git add <file>..." to include in what will be committed)
      team.html

  nothing added to commit but untracked files present (use "git add" to track)
  ```

  - commit and push those changes

  ```
  😹 🍒 :git-exercises ivy$ git add .
  😹 🍒 :git-exercises ivy$ git commit -m 'Set the team file'
  [ft/team-page 760be4d] Set the team file
  1 file changed, 14 insertions(+)
  create mode 100644 team.html
  😹 🍒 :git-exercises ivy$     git push --set-upstream origin ft/team-page
  Enumerating objects: 4, done.
  Counting objects: 100% (4/4), done.
  Delta compression using up to 8 threads
  Compressing objects: 100% (3/3), done.
  Writing objects: 100% (3/3), 449 bytes | 449.00 KiB/s, done.
  Total 3 (delta 1), reused 0 (delta 0), pack-reused 0
  remote: Resolving deltas: 100% (1/1), completed with 1 local object.
  remote:
  remote: Create a pull request for 'ft/team-page' on GitHub by visiting:
  remote:      https://github.com/IvyMurage/git-exercises/pull/new/ft/team-page
  remote:
  To github.com:IvyMurage/git-exercises.git
  * [new branch]      ft/team-page -> ft/team-page
  Branch 'ft/team-page' set up to track remote branch 'ft/team-page' from 'origin'.
  ```

  - Create a new PR for the changes
    ![plot](/images/Screenshot%20from%202024-04-22%2015-36-01.png)

  - Go back to main branch (checkout the main branch)

  ```
    😹 🍒 :git-exercises ivy$ git checkout main
    Switched to branch 'main'
    Your branch is up to date with 'origin/main'.
    😹 🍒 :git-exercises ivy$ git branch
    dev
    ft/bundle-2
    ft/service-redesign
    ft/team-page
    * main
  ```

  - Create new branch named ft/contact-page

  ```
    😹 🍒 :git-exercises ivy$ git switch -c ft/contact-page
    Switched to a new branch 'ft/contact-page'
  ```

  - Go back to the ft/team-page

  ```
    😹 🍒 :git-exercises ivy$ git switch ft/team-page
    Switched to branch 'ft/team-page'
    Your branch is up to date with 'origin/ft/team-page'.
    😹 🍒 :git-exercises ivy$ git branch
    dev
    ft/bundle-2
    ft/contact-page
    ft/service-redesign
    * ft/team-page
    main
  ```

  - With the help of git log look for the last commit and copy its hash

  ```
  😹 🍒 :git-exercises ivy$ git log
    commit 760be4d99f50c0a377f18e1ec909d93669ca9b04 (HEAD -> ft/team-page, origin/ft/team-page)
    Author: Murage-Ivy <ivymurage2000@gmail.com>
    Date:   Mon Apr 22 15:27:15 2024 +0200

        Set the team file

    commit e107ad64f788578b26ead589f5af967daffe8dc5 (origin/main, main, ft/contact-page)
    Merge: 270df24 3e25c3d
    Author: Murage-Ivy <ivymurage2000@gmail.com>
    Date:   Mon Apr 22 15:06:54 2024 +0200

        resolve conflict

    commit 270df24e49b049a62a334aa4cf255c3625719872
    Author: Murage-Ivy <ivymurage2000@gmail.com>
    Date:   Mon Apr 22 15:03:28 2024 +0200
  ```

  - Checkout again ft/contact-page using git cherry-pick get the changes from the last commit on the ft/team-page branch.

  ```
    😹 🍒 :git-exercises ivy$ git checkout ft/contact-page
    Switched to branch 'ft/contact-page'
    😹 🍒 :git-exercises ivy$ git branch
    dev
    ft/bundle-2
    * ft/contact-page
    ft/service-redesign
    ft/team-page
    main
    😹 🍒 :git-exercises ivy$ git cherry-pick 760be4d99f50c0a377f18e1ec909d93669ca9b04
    [ft/contact-page f81297c] Set the team file
    Date: Mon Apr 22 15:27:15 2024 +0200
    1 file changed, 14 insertions(+)
    create mode 100644 team.html
  ```

  - Add new changes for the contact page and commit, push them

  ```
    😹 🍒 :git-exercises ivy$ touch contact.html
    😹 🍒 :git-exercises ivy$ git branch
    dev
    ft/bundle-2
    * ft/contact-page
    ft/service-redesign
    ft/team-page
    main
    😹 🍒 :git-exercises ivy$ git add .
    😹 🍒 :git-exercises ivy$ git commit -m ' Set the contact page'
    [ft/contact-page 3c0df17]  Set the contact page
    1 file changed, 14 insertions(+)
    create mode 100644 contact.html
    😹 🍒 :git-exercises ivy$ git push
    fatal: The current branch ft/contact-page has no upstream branch.
    To push the current branch and set the remote as upstream, use

        git push --set-upstream origin ft/contact-page

    😹 🍒 :git-exercises ivy$     git push --set-upstream origin ft/contact-page
    Enumerating objects: 7, done.
    Counting objects: 100% (7/7), done.
    Delta compression using up to 8 threads
    Compressing objects: 100% (6/6), done.
    Writing objects: 100% (6/6), 730 bytes | 365.00 KiB/s, done.
    Total 6 (delta 3), reused 0 (delta 0), pack-reused 0
    remote: Resolving deltas: 100% (3/3), completed with 1 local object.
    remote:
    remote: Create a pull request for 'ft/contact-page' on GitHub by visiting:
    remote:      https://github.com/IvyMurage/git-exercises/pull/new/ft/contact-page
    remote:
    To github.com:IvyMurage/git-exercises.git
    * [new branch]      ft/contact-page -> ft/contact-page
    Branch 'ft/contact-page' set up to track remote branch 'ft/contact-page' from 'origin'.
  ```

  - Create a new PR for the contact page
    ![plot](/images/Screenshot%20from%202024-04-22%2016-22-56.png)

  - From the ft/contact-page branch create a new branch called ft/faq-page

  ```
  😹 🍒 :git-exercises ivy$ git switch -c ft/faq-page
    Switched to a new branch 'ft/faq-page'
  ```

  - Create a new faq.html page and add some changes there

  ```
    😹 🍒 :git-exercises ivy$ touch faq.html
    😹 🍒 :git-exercises ivy$ git status
    On branch ft/faq-page
    Untracked files:
    (use "git add <file>..." to include in what will be committed)
        faq.html
  ```

  - Commit and push those changes

  ```
    😹 🍒 :git-exercises ivy$ git add .
    😹 🍒 :git-exercises ivy$ git commit -m 'set faq file'
    [ft/faq-page c3f1e15] set faq file
    1 file changed, 14 insertions(+)
    create mode 100644 faq.html
    😹 🍒 :git-exercises ivy$ git push
    fatal: The current branch ft/faq-page has no upstream branch.
    To push the current branch and set the remote as upstream, use

        git push --set-upstream origin ft/faq-page

    😹 🍒 :git-exercises ivy$     git push --set-upstream origin ft/faq-page
    Enumerating objects: 4, done.
    Counting objects: 100% (4/4), done.
    Delta compression using up to 8 threads
    Compressing objects: 100% (3/3), done.
    Writing objects: 100% (3/3), 439 bytes | 439.00 KiB/s, done.
    Total 3 (delta 1), reused 0 (delta 0), pack-reused 0
    remote: Resolving deltas: 100% (1/1), completed with 1 local object.
    remote:
    remote: Create a pull request for 'ft/faq-page' on GitHub by visiting:
    remote:      https://github.com/IvyMurage/git-exercises/pull/new/ft/faq-page
    remote:
    To github.com:IvyMurage/git-exercises.git
    * [new branch]      ft/faq-page -> ft/faq-page
    Branch 'ft/faq-page' set up to track remote branch 'ft/faq-page' from 'origin'.
  ```

  - Using git revert, revert the changes of the last commit of the ft/team-page branch. (use the commit hash you copied earlier)

  ```
  😹 🍒 :git-exercises ivy$ git revert 760be4d99f50c0a377f18e1ec909d93669ca9b04
    [ft/faq-page 716f478] Revert "Set the team file"
    1 file changed, 14 deletions(-)
    delete mode 100644 team.html
  ```

  - Push the changes and create a new PR
    ![plot](/images/Screenshot%20from%202024-04-22%2016-21-27.png)

  ```
      😹 🍒 :git-exercises ivy$ git status
    On branch ft/faq-page
    Your branch is ahead of 'origin/ft/faq-page' by 1 commit.
    (use "git push" to publish your local commits)

    nothing to commit, working tree clean
    😹 🍒 :git-exercises ivy$ git push
    Enumerating objects: 3, done.
    Counting objects: 100% (3/3), done.
    Delta compression using up to 8 threads
    Compressing objects: 100% (2/2), done.
    Writing objects: 100% (2/2), 278 bytes | 278.00 KiB/s, done.
    Total 2 (delta 1), reused 0 (delta 0), pack-reused 0
    remote: Resolving deltas: 100% (1/1), completed with 1 local object.
    To github.com:IvyMurage/git-exercises.git
    c3f1e15..716f478  ft/faq-page -> ft/faq-page
  ```

### Exercise 2

- Question 1:

  - Create new branch from the ft/faq-page branch named ft/home-page-redesign

  ```
  😹 🍒 :git-exercises ivy$ git switch -c ft/home-page-redesign
  Switched to a new branch 'ft/home-page-redesign'
  ```

  - Go back to the main branch and make some changes there

  ```
    😹 🍒 :git-exercises ivy$ git switch main
    Switched to branch 'main'
    Your branch is up to date with 'origin/main'.

    😹 🍒 :git-exercises ivy$ git status
    On branch main
    Your branch is up to date with 'origin/main'.

    Changes not staged for commit:
    (use "git add <file>..." to update what will be committed)
    (use "git restore <file>..." to discard changes in working directory)
        modified:   home.html

    no changes added to commit (use "git add" and/or "git commit -a")
  ```

  - Commit and push them

    ```
    😹 🍒 :git-exercises ivy$ git add .
        😹 🍒 :git-exercises ivy$ git commit -m 'Update home page'
        [main aad9dc9] Update home page
        1 file changed, 1 insertion(+), 1 deletion(-)
        😹 🍒 :git-exercises ivy$ git push
        Enumerating objects: 5, done.
        Counting objects: 100% (5/5), done.
        Delta compression using up to 8 threads
        Compressing objects: 100% (3/3), done.
        Writing objects: 100% (3/3), 318 bytes | 318.00 KiB/s, done.
        Total 3 (delta 2), reused 0 (delta 0), pack-reused 0
        remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
        To github.com:IvyMurage/git-exercises.git
        e107ad6..aad9dc9  main -> main
    ```

- go back to the ft/home-page-redesign branch

  ```
  😹 🍒 :git-exercises ivy$ git switch ft/home-page-redesign
  Switched to branch 'ft/home-page-redesign'
  😹 🍒 :git-exercises ivy$ git branch
  dev
  ft/bundle-2
  ft/contact-page
  ft/faq-page
  * ft/home-page-redesign
  ft/service-redesign
  ft/team-page
  main
  ```

* Using git rebase, rebase your branch to main

  ```
  😹 🍒 :git-exercises ivy$ git rebase main
  Successfully rebased and updated refs/heads/ft/home-page-redesign.
  ```

* Add changes to the home page and commit push them

  ```
  😹 🍒 :git-exercises ivy$ git status
  On branch ft/home-page-redesign
  Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
      modified:   home.html

  no changes added to commit (use "git add" and/or "git commit -a")
  😹 🍒 :git-exercises ivy$ git add .
  😹 🍒 :git-exercises ivy$ git commit -m 'Update home page'
  [ft/home-page-redesign 446d165] Update home page
  1 file changed, 1 insertion(+)
  😹 🍒 :git-exercises ivy$ git push --set-upstream origin ft/home-page-redesign
  Enumerating objects: 16, done.
  Counting objects: 100% (16/16), done.
  Delta compression using up to 8 threads
  Compressing objects: 100% (14/14), done.
  Writing objects: 100% (14/14), 1.54 KiB | 786.00 KiB/s, done.
  Total 14 (delta 7), reused 0 (delta 0), pack-reused 0
  remote: Resolving deltas: 100% (7/7), completed with 1 local object.
  remote:
  remote: Create a pull request for 'ft/home-page-redesign' on GitHub by visiting:
  remote:      https://github.com/IvyMurage/git-exercises/pull/new/ft/home-page-redesign
  remote:
  To github.com:IvyMurage/git-exercises.git
  * [new branch]      ft/home-page-redesign -> ft/home-page-redesign
  Branch 'ft/home-page-redesign' set up to track remote branch 'ft/home-page-redesign' from 'origin'.
  ```

* Create a PR for the changes.
  ![plot](/images/Screenshot%20from%202024-04-22%2016-44-58.png)

## Bundle 4

### Exercise 1

- Checkout the main branch

  ```
  😹 🍒 :git-exercises ivy$ git switch main
  Switched to branch 'main'
  Your branch is up to date with 'origin/main'.
  ```

- - Create a new repository on github
  - Using git remote add the repo to your project as second remote named `git-copy`

  ```
  😹 🍒 :git-exercises ivy$ git remote add git-copy git@github.com:IvyMurage/git-exercise-copy.git
  😹 🍒 :git-exercises ivy$ git remote -v
  git-copy	git@github.com:IvyMurage/git-exercise-copy.git (fetch)
  git-copy	git@github.com:IvyMurage/git-exercise-copy.git (push)
  origin	git@github.com:IvyMurage/git-exercises.git (fetch)
  origin	git@github.com:IvyMurage/git-exercises.git (push)
  ```

- Make a new changes on the home page

  ```
  😹 🍒 :git-exercises ivy$ git status
  On branch main
  Your branch is up to date with 'origin/main'.

  Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
      modified:   home.html

  no changes added to commit (use "git add" and/or "git commit -a")
  ```

- Commit the changes

  ```
  😹 🍒 :git-exercises ivy$ git add .
  😹 🍒 :git-exercises ivy$ git commit -m 'Update home page'
  [main 51b1756] Update home page
  1 file changed, 1 insertion(+)
  😹 🍒 :git-exercises ivy$ git push -u origin main
  Enumerating objects: 5, done.
  Counting objects: 100% (5/5), done.
  Delta compression using up to 8 threads
  Compressing objects: 100% (3/3), done.
  Writing objects: 100% (3/3), 322 bytes | 322.00 KiB/s, done.
  Total 3 (delta 2), reused 0 (delta 0), pack-reused 0
  remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
  To github.com:IvyMurage/git-exercises.git
  aad9dc9..51b1756  main -> main
  Branch 'main' set up to track remote branch 'main' from 'origin'.
  ```

- Push the changes to the both remotes. the origin and git-copy

  ```
      😹 🍒 :git-exercises ivy$ git push -u origin main
      Enumerating objects: 5, done.
      Counting objects: 100% (5/5), done.
      Delta compression using up to 8 threads
      Compressing objects: 100% (3/3), done.
      Writing objects: 100% (3/3), 322 bytes | 322.00 KiB/s, done.
      Total 3 (delta 2), reused 0 (delta 0), pack-reused 0
      remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
      To github.com:IvyMurage/git-exercises.git
      aad9dc9..51b1756  main -> main
      Branch 'main' set up to track remote branch 'main' from 'origin'.
      😹 🍒 :git-exercises ivy$ git push -u git-copy main
      Enumerating objects: 37, done.
      Counting objects: 100% (37/37), done.
      Delta compression using up to 8 threads
      Compressing objects: 100% (35/35), done.
      Writing objects: 100% (37/37), 4.10 KiB | 420.00 KiB/s, done.
      Total 37 (delta 21), reused 0 (delta 0), pack-reused 0
      remote: Resolving deltas: 100% (21/21), done.
      To github.com:IvyMurage/git-exercise-copy.git
      * [new branch]      main -> main
      Branch 'main' set up to track remote branch 'main' from 'git-copy'.
  ```

### Exercise 2

- Checkout a new branch named ft/footer

```
😹 🍒 :git-exercises ivy$ git switch -c ft/footer
Switched to a new branch 'ft/footer'
```

- Add some changes to the branch and commit them

  ```
      Switched to a new branch 'ft/footer'
      😹 🍒 :git-exercises ivy$ touch footer.html
      😹 🍒 :git-exercises ivy$ git add .
      😹 🍒 :git-exercises ivy$ git commit -m 'Create footer'
      [ft/footer c8d7a8e] Create footer
      1 file changed, 16 insertions(+)
      create mode 100644 footer.html
      😹 🍒 :git-exercises ivy$ git status
      On branch ft/footer
      Changes not staged for commit:
      (use "git add <file>..." to update what will be committed)
      (use "git restore <file>..." to discard changes in working directory)
          modified:   footer.html

      no changes added to commit (use "git add" and/or "git commit -a")


  ```

* Add more changes again to the branch and create a second commit

  ````
        😹 🍒 :git-exercises ivy$ git add .
    😹 🍒 :git-exercises ivy$ git commit -m 'Add terms and conditions'
    [ft/footer 9397c01] Add terms and conditions
    1 file changed, 1 insertion(+)
    ```
  ````

* Push and create a new PR for the branch

  ```
  😹 🍒 :git-exercises ivy$ git push --set-upstream origin ft/footer
  Enumerating objects: 7, done.
  Counting objects: 100% (7/7), done.
  Delta compression using up to 8 threads
  Compressing objects: 100% (6/6), done.
  Writing objects: 100% (6/6), 740 bytes | 370.00 KiB/s, done.
  Total 6 (delta 3), reused 0 (delta 0), pack-reused 0
  remote: Resolving deltas: 100% (3/3), completed with 1 local object.
  remote:
  remote: Create a pull request for 'ft/footer' on GitHub by visiting:
  remote: https://github.com/IvyMurage/git-exercises/pull/new/ft/footer
  remote:
  To github.com:IvyMurage/git-exercises.git
    [new branch] ft/footer -> ft/footer
  Branch 'ft/footer' set up to track remote branch 'ft/footer' from 'origin'.
  ```

* Checkout the main branch again
  ```
  😹 🍒 :git-exercises ivy$ git switch main
  Switched to branch 'main'
  Your branch is up to date with 'git-copy/main'.
  ```
* From there create a new branch named ft/squashing

  ```
  😹 🍒 :git-exercises ivy$ git switch -c ft/squashing
  Switched to a new branch 'ft/squashing'
  😹 🍒 :git-exercises ivy$ git branch
  dev
  ft/bundle-2
  ft/contact-page
  ft/faq-page
  ft/footer
  ft/home-page-redesign
  ft/service-redesign
  * ft/squashing
  ft/team-page
  main
  ```

* Using git merge squash, squash the changes on the ft/footer branch
  ```
  😹 🍒 :git-exercises ivy$ git merge --squash ft/footer
  Updating 51b1756..9397c01
  Fast-forward
  Squash commit -- not updating HEAD
  footer.html | 17 +++++++++++++++++
  1 file changed, 17 insertions(+)
  create mode 100644 footer.html
  ```
* Commit the changes with a different commit message such as footer changes squashing

  ```
  😹 🍒 :git-exercises ivy$ git status
  On branch ft/squashing
  Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
  new file: footer.html

  😹 🍒 :git-exercises ivy$ git add .
  😹 🍒 :git-exercises ivy$ git commit -m 'footer changes squashing'
  [ft/squashing 6f86101] footer changes squashing
  1 file changed, 17 insertions(+)
  create mode 100644 footer.html
  😹 🍒 :git-exercises ivy$ git push
  fatal: The current branch ft/squashing has no upstream branch.
  To push the current branch and set the remote as upstream, use
  git push --set-upstream origin ft/squashing
  ```

* Push the changes and create a PR
  ```
  😹 🍒 :git-exercises ivy$ git push --set-upstream origin ft/squashing
  Enumerating objects: 4, done.
  Counting objects: 100% (4/4), done.
  Delta compression using up to 8 threads
  Compressing objects: 100% (3/3), done.
  Writing objects: 100% (3/3), 489 bytes | 489.00 KiB/s, done.
  Total 3 (delta 1), reused 0 (delta 0), pack-reused 0
  remote: Resolving deltas: 100% (1/1), completed with 1 local object.
  remote:
  remote: Create a pull request for 'ft/squashing' on GitHub by visiting:
  remote:      https://github.com/IvyMurage/git-exercises/pull/new/ft/squashing
  remote:
  To github.com:IvyMurage/git-exercises.git
  * [new branch]      ft/squashing -> ft/squashing
  Branch 'ft/squashing' set up to track remote branch 'ft/squashing' from 'origin'.
  ```

## Bundle 5

### Exercises 1

- Clone your fork on your machine

  ```
      😹 🍒 :ojemba ivy$ git clone git@github.com:IvyMurage/git-cafe-exercise.git
      Cloning into 'git-cafe-exercise'...
      remote: Enumerating objects: 107, done.
      remote: Counting objects: 100% (14/14), done.
      remote: Compressing objects: 100% (10/10), done.
      remote: Total 107 (delta 5), reused 4 (delta 4), pack-reused 93
      Receiving objects: 100% (107/107), 1.95 MiB | 768.00 KiB/s, done.
      Resolving deltas: 100% (5/5), done.
  ```

* - Edit the `index.html` file
  - Change the text `Welcome to our place` to `Welcome to our restaurant`
  - Commit and push the changes

  ```
  😹 🍒 :ojemba ivy$ cd git-cafe-exercise/
  😹 🍒 :git-cafe-exercise ivy$ code .
  😹 🍒 :git-cafe-exercise ivy$ git add .
  😹 🍒 :git-cafe-exercise ivy$ git commit -m 'Change header'
  [main ecf6127] Change header
  1 file changed, 345 insertions(+), 288 deletions(-)
  rewrite index.html (85%)
  😹 🍒 :git-cafe-exercise ivy$ git push
  Enumerating objects: 5, done.
  Counting objects: 100% (5/5), done.
  Delta compression using up to 8 threads
  Compressing objects: 100% (3/3), done.
  Writing objects: 100% (3/3), 1.38 KiB | 472.00 KiB/s, done.
  Total 3 (delta 2), reused 0 (delta 0), pack-reused 0
  remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
  To github.com:IvyMurage/git-cafe-exercise.git
  d1d3f9c..ecf6127  main -> main
  ```

* Create a PR for the changes.
  ![plot](/images/Screenshot%20from%202024-04-22%2019-17-03.png)

## Bundle 6

### Exercises 1

- On the git-cafe-exercise repo create a new feature branch

  ```
  😹 🍒 :git-cafe-exercise ivy$ git switch -c ft-menu-branch
  Switched to a new branch 'ft-menu-branch'
  ```

- Add new changes related to a new page named Menu

  ```
  😹 🍒 :git-cafe-exercise ivy$ git add .
  😹 🍒 :git-cafe-exercise ivy$ git commit -m 'create menu page'
  [ft-menu-branch 9831f68] create menu page
  1 file changed, 15 insertions(+)
  create mode 100644 menu.html
  😹 🍒 :git-cafe-exercise ivy$ git push
  fatal: The current branch ft-menu-branch has no upstream branch.
  To push the current branch and set the remote as upstream, use

      git push --set-upstream origin ft-menu-branch

  😹 🍒 :git-cafe-exercise ivy$     git push --set-upstream origin ft-menu-branch
  Enumerating objects: 4, done.
  Counting objects: 100% (4/4), done.
  Delta compression using up to 8 threads
  Compressing objects: 100% (3/3), done.
  Writing objects: 100% (3/3), 466 bytes | 466.00 KiB/s, done.
  Total 3 (delta 1), reused 0 (delta 0), pack-reused 0
  remote: Resolving deltas: 100% (1/1), completed with 1 local object.
  remote:
  remote: Create a pull request for 'ft-menu-branch' on GitHub by visiting:
  remote:      https://github.com/IvyMurage/git-cafe-exercise/pull/new/ft-menu-branch
  remote:
  To github.com:IvyMurage/git-cafe-exercise.git
  * [new branch]      ft-menu-branch -> ft-menu-branch
  Branch 'ft-menu-branch' set up to track remote branch 'ft-menu-branch' from 'origin'.

  ```

### Exercise 3

- On the `git-cafe-exercise` repo, there is a small hotfix on the contact page
- Change the telephone on the `index-4.html` page from `+1 800 603 6035` to `+1 800 659 6035`

  ![alt text](image.png)
