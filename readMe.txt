0. make your global config:
    git config --global user.name "Alireza Rezaei"
    git config --global user.email "alireza.rezaeikalat@gmail.com"
    git config --list

    git <verb> --help       : git config --help

1. to make git repository
      <!-- git init-->

2. to see the status of files:
      <!-- git status -->
      <!-- git diff -->   (you can see the changes by this command)

3. to discard changes in working directory
      <!-- git restore <filename>-->

4. to add to stage area
      <!-- git add <index.html> -->
  to add all the files to staging area
      <!-- git add -A -->

5. to remove from stage area
      <!-- git rm --cached <index.html> -->
  
  or
      <!-- git reset <filename> -->
  to remove all the files from staging area-->
      <!-- git reset -->

6. to commit
      <!-- git commit -m '<description>' -->

7. to see the commit history
      <!-- git log -->
      <!-- git log -oneline -->

8. to go back in time in read only mode
      <!-- git checkout <commit id that you want go to>-->

9. <!--!!! to make a new commit and undo particular one -->
      <!-- git revert <commit id that you want to undo>-->

10. to go to special commit and delete the after ones but the changes is visible in editor:
    
        a. <!-- git reset <commit id that you want go to> -->

    to reset and remove the changes from editor:
        b. <!-- git reset <commit id that you want go to> --hard -->

11. to make a new branch 
      <!-- git branch <branch name>-->

12. to delete the branch first switch to master branch then:
      <!-- git branch -d <branch name>-->

13. to see the tree of files 
    (*) shows the current branch 
      
          <!-- git branch -a -->
        or 
    to see all branches locally 
          <!-- git branch -->

14. to go to branches
      <!-- git checkout <branch name>-->

15. to merge the branch to master branch 
 
    first you have to go to master branch 
        <!-- git checkout master -->

    you can see all the merged branch
        <!-- git branch --merged -->

    Then you can merge
        <!-- git merge <name of the branch that you want to merge to master> -->

    if you have the conflict first remove the comments 
    then commit with: 
        a. <!-- git add . -->
        b. <!-- git commit -->
      
    to quit
      a. <!-- shift + : -->
      b. <!-- wq -->
    
    [ATTENTION]
    We have two types of merge:

        a. fast forward merge: It just change the current branch tip to -F and combines histories of two branch 

                            -D - E -F 
                A - B - C 
        
        b. three way merge (git uses 3 commits to generate the merge commit- head of two branch and common ancestor)
    
    [ATTENTION]
    If you are in the middle of merge, you stop it completely:

        git merge --abort

16. to push to the remote repository

    first commite the changes in your local repository
        a. <!-- git add . -->
        b. <!-- git commit -m <description> -->

    to push
        a. <!-- git push <url or origin name> <branch to push> -->

17. to make alias for the url of the remote repository 
        <!-- git remote add <alias> <url> -->
  
    to see the alias name
        <!-- git remote -v -->

18. to clone the repository
        <!-- git clone <url> <where to clone> -->
        <!-- !!! and also makes origin alias -->


//////////////// a common workflow for working in the team //////////
19. Working in the team
    first update your local repo
        <!-- git pull origin master -->

  then make a new branch to make changes in that branch
        <!-- git branch <branch name> -->
        <!-- git checkout <branch name> -->

  after your changes push the new branch to remote repo 
        <!-- git push -u origin <branch name> -->

  Then make pull request to merge it to master branch in github site
  Then the manager can accept the changes 

if you have the permission to push the master branch: 

  after accepting the branch, you can merge the branch locally 
  go to master branch
    <!-- git checkout master -->
    <!-- git pull origin master -->

  merge the branch
    <!-- git merge <branch name> -->

  now push the master branch 
    <!-- git push origin master -->

now you can delete the branch locally:    <pay attention to the locally>

  deleting the branch 
    git branch -d <branch name>

  but if you see the branches the remote branch is still there 
    <!-- git branch -a -->
  
  to delete the branch on remote repository 
    <!-- git push origin --delete <branch name> -->

//////// fixing mistakes in git //////////

20. if you add a commit with wrong message, you can change the commit message of the last one:  

    git commit --amend -m 'new message'     but in this way you will change the commit hash

    git commit --amend                      for example if you left a file from commit first add it then use --amend 
                                            (and the commit hash will be different)


    (so do this, if you haven't push your commit to the remote repository)

  
21. if you commit to a wrong branch, you can add the commit to the right branch and remove the commit from the wrong branch:

    a. first get the commit hash from the wrong branch:

          git log     (then copy the id)
    
    b. then go to the right branch: 

          git checkout <right branch name>
    
    c. copy the commit to the right branch:

          git cherry-pick <commit id>

    d. delete the commit on the wrong branch:

        git checkout <wrong branch>
        git reset --soft <the previous commit id>     --soft  reset the changes but keep the changes in the staging area


        git reset <the previous commit id>            --mixed this is the default one, reset the changes and remove from the staging
                                                      area but keep it in the editor
        
        git reset --hard <the previous commit id>     --hard removes the changes and remove it from staging area and the editor as well
                                                      but it will not removed the untacked files, for example if you add another file
                                                      that is not in the commit that you reset to. so you have to delete this file 
                                                      manually or use another instruction:

                                                      git clean -df       (-d for directory and -f for files)


22. if you remove the commit using git reset --hard you can still access the deleted commit: 

      a. first get the hash code of the deleted commit: 

          git reflog
      
      b. then go to the deleted commit in detached head:

          git checkout <the deleted commit id>      (now you are in the detached head)

      c. then make new branch to save attach head to this     (cat .git/HEAD)

          git checkout -b <your new branch name>

      d. then if you want, merge the branch to the master branch:

          git checkout master
          git merge <branch name> 


23. if you are in a situation that you push your commits, and other people pull your commits, it is not good practise to change the 
      git history by using reset or ammend, in this situations you can use revert: 

          git revert <commit id that you want ro revert>


/////////// using git stash ////////////

24. if you want to remove your changes temporary before commit, and can get them back, when you want, you can use: 

        git stash save "your message"

25. you can get the list of stashes:

        git stash list

26. you can reapply the stash: 

        git stash apply <stash@{0}>             // but the stash is still in the stash list

        git stash pop                        // get the latest stash and remove it from stash list

26. remove the stash from stash list

        git stash drop <stash@{0}>

27. to remove all the stashes:  

        git stash clear

[ATTENTION]
28. using stash is a good way, to fixed the common error when you make changes on the wrong branch: 

        a. you make changes to wrong branch but you haven't commit it, but when you want to change your branch, you will get an 
            error that is you have uncommited change, so you can stash your changes: 

                git stash save "wrong change in the master branch"

        b. go to the branch that is right: 

                git checkout <branch name>

        c. apply the stash: 

                git stash pop


/////////// using diff merge tool ////////

29. first download DiffMerge

30. config your git for gitmerge:

        git config --global diff.tool diffmerge
        git config --global difftool.diffmerge.cmd 'diffmerge "$LOCAL" "$REMOTE"'
        git config --global merge.tool diffmerge
        git config --global mergetool.diffmerge.cmd 'diffmerge --merge --result="$MERGED" "$LOCAL" "$(if test -f "$BASE"; then echo "$BASE"; else echo "$LOCAL"; fi)" "$REMOTE"'
        git config --global mergetool.diffmerge.trustExitCode true

31. opening difftool:

        git difftool


32. you can use merge tool:

        git mergetool


//// different between git add //////////

33. git add -A          (it is going to add all the modified files, deleted files, and new files in all tree of files)

    git add -A mydir/       (only in the mydir folder) (git add -A is the default behavior for git)

    git add -u          (add only modified and deleted files not new files in all tree)

    git add .           (add all the files in current directory, because the default behavior is -A)


///////////// using tags in git ////////////

34. Git has the ability to tag specific points in a repository’s history as being important. Typically, people use this
     functionality to mark release points (v1.0, v2.0 and so on). working with tags are just like working with branches

    a. list all the tags:

            git tag   (optional -l or --list)
    
    b. list tags with special pattern:

            git tag -l "v1.8.5*"
    
    c. creating annotated tag:

        git tag -a v1.4 -m 'my version 1.4'

        see the tag information:

            git show v1.4

                tagger: ...
                date: ....
        
    d. create lightweight tag:

        git tag v.14

        see the tag:
            git show v.14
    
    e. tagging later (you can tag older commits)

        git tag -a v1.3 <commit id>
    

    f. after making tags, you have to push tags to remote servers, like branches:

        git push origin <tag name>

        to push all your tags:

        git push origin --tags
    
    g. deleting tags;
        
        git tag -d <tag name>

        delete on the remote server:

            git push origin --delete <tag name>
    
    h. to check out to the tag

        git checkout <tagname>

        but in this situation you are in the detach head, so you have to make new branch to save your commits
    
