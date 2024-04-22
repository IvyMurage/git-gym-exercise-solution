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
* Question 1:
    
    * Create a new home.html file, add some html changes and save them
    ```
    😹 🍒 :git-exercises ivy$ touch home.html
    😹 🍒 :git-exercises ivy$ git status
    On branch dev
    Untracked files:
    (use "git add <file>..." to include in what will be committed)
        home.html

    nothing added to commit but untracked files present (use "git add" to track)
    ```

    * Stash save your current changes
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

    * Repeat the same process for a new about page and stash save your changes
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

    * Repeat the same process for a new team page and stash save your changes
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

    * Using stash pop restore the changes of the about page
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
    * With the help of an index use stash pop bring back the home page changes
    ```
    😹 🍒 :git-exercises ivy$ git stash pop 1
    On branch dev
    Changes to be committed:
    (use "git restore --staged <file>..." to unstage)
        new file:   about.html
        new file:   home.html

    Dropped refs/stash@{1} (f45c6f3ab707a41843045e3ebec1f49c2313c84c)
    ```
    
    * Commit the current changes and push them
    ```
    git commit -m 'Add home and about page'
    [dev 206df2b] Add home and about page
    2 files changed, 25 insertions(+)
    create mode 100644 about.html
    create mode 100644 home.html
    ```

    * Using stash pop restore the changes of the team page index
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
    * Reset the current changes using git reset and go back to the changes without the team page
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
* Question 1:
    * Create a new branch named ft/bundle-2:
    ```
    😹 🍒 :git-exercises ivy$ git switch -c ft/bundle-2
    Switched to a new branch 'ft/bundle-2'
    😹 🍒 :git-exercises ivy$ git branch
    dev
    * ft/bundle-2
    main
    ```
    * Add new changes to your project. create a new page named services.html and add some changes 
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
    * Commit your changes and create a Pull Request against the main branch in your github repository
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

    * Request a review and make sure your Pull request gets merged (Look for someone to merge your PR)

    ![plot](/images/Screenshot%20from%202024-04-22%2013-32-45.png)
