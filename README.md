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
