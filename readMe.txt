1. <!--!!! to make git repository -->
  <!-- git init-->

2. <!--!!! to see the status of files: -->
  <!-- git status -->

3. <!--!!! to discard changes in working directory-->
  <!-- git restore <filename>-->

4. <!--!!! to add to stage area -->
  <!-- git add <index.html> -->

5. <!--!!! to remove from stage area -->
  <!-- git rm --cached <index.html> -->

6. <!--!!! to see the commit history-->
  <!-- git commit -m '<description>' -->

7. <!--!!! to see the commit history-->
  <!-- git log -->
  <!-- git log -oneline -->

8. <!--!!! to go back in time in read only mode-->
  <!-- git checkout <commit id>-->

9. <!--!!! to make a new commit and undo particular one -->
  <!-- git revert <commit id>-->

10. <!--!!! to go to special commit and delete the after ones but the changes is visible in editor -->
    
  a. <!-- git reset <commit id>-->
  <!--!!! to reset and remove the changes from editor-->
    b. <!-- git reset <commit id> --hard -->

11. <!--!!! to make a new branch -->
    <!-- git branch <branch name>-->

12. <!--!!! to delete the branch first switch to master branch then: -->
    <!-- git branch -d <branch name>-->

13. <!--!!! to see the tree of files -->
    <!--!!! (*) shows the current branch -->
    <!-- git branch -a -->

14. <!--!!! to go to branches-->
    <!-- git checkout <branch name>-->

15. <!--!!! to merge the branch to master branch-->
    <!--!!! first you have to go to master branch-->
    <!-- git merge <name of the branch> -->

    <!-- !!! if you have the conflict first remove the comments -->
    <!-- !!! then commit with -->
      a. <!-- git add . -->
      b. <!-- git commit -->
    
    <!-- !!! to quit -->
      a. <!-- shift + : -->
      b. <!-- wq -->

16. <!-- !!! to push to the remote repository -->

    <!-- !!! first commite the changes in your local repository -->
      a. <!-- git add . -->
      b. <!-- git commit <description> -->

    <!-- !!! to push -->
      a. <!-- git push <url or origin name> <branch to push> -->

17. <!-- !!! to make alias for the url of the remote repository -->
  <!-- git remote add <alias> <url> -->
  
  <!-- !!! to see the alias name -->
    <!-- git remote -v -->

18. <!-- !!! to clone the repository -->
  <!-- git clone <url> -->
  <!-- !!! and also makes origin alias -->




19. <!-- !!! Working in the team -->
  <!-- !!! first update your local repo -->
  <!-- git pull origin master -->

  <!-- !!! then make a new branch to make changes in that branch -->
  <!-- !!! push the new branch to remote repo -->
    <!-- git push origin <branch name> -->

  <!-- !!! Then make pull request to merge it to master branch in github site -->
  <!-- !!! Then the manager can accept the changes -->
