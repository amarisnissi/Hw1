# Hw1
## ICP2017F - Introduction to Computer Programming (Fall 2017)  

**Name:** <first name> <last name>
  
**UT EID:** <your UT EID>
  
**Email:** <your email>
  
**Department:** Department of Aerospace Engineering and Engineering Mechanics

**University:** The University of Texas at Austin

**Level:** Undergraduate - <Freshman(1st year) / Sophomore(2nd year) / Junior(3rd year) / Senior(4th year)>

**ICP Class Position:** Student

**Course Webpage:** http://www.shahmoradi.org/ICP2017F/

**Photo:**

Amir Shahmoradi

## Description of the project’s content  

This repository contains my homework, quizzes, and virtually every effort that I have made for **ICP2017F class**. The structure of the project is the following:

- [Homework](Homework/): (the homework hyperlink should take the reader to the homework folder)
This directory contains all my homework submissions, each of which is a folder properly named with homework number, containing the homework submission.

 - [Quiz](quiz/): (the quiz hyperlink should take the reader to the quizzes folder)
This directory contains all my quiz submissions, each of which is a folder properly named with quiz number, containing the quiz submission.

- [Exam](Exam/): (the exam hyperlink should take the reader to the exams folder)
This directory contains all my exam submissions, each of which is a folder properly named with exam name or number, containing the exam submission.

For questions and troubleshooting, please contact:

<your name>
<your email>
<any other contact or signature information that you would like to add>

># "I have not failed. I’ve just found 10,000 ways that won’t work.
># Thomas A. Edison

#Part II of the Homework
A) C:\Projects COE\Hw1>git branch
* master

C:\Projects COE\Hw1>git branch test1

C:\Projects COE\Hw1>git branch
* master
  test1

C:\Projects COE\Hw1>git branch test2

C:\Projects COE\Hw1>git branch
* master
  test1
  test2
  
B)C:\Projects COE\Hw1>git checkout test1
Switched to branch 'test1'
C:\Projects COE\Hw1>cd Homework/1/

C:\Projects COE\Hw1\Homework\1>dir
 Volume in drive C is Windows
 Volume Serial Number is 1836-B444

 Directory of C:\Projects COE\Hw1\Homework\1

09/17/2017  10:59 AM    <DIR>          .
09/17/2017  10:59 AM    <DIR>          ..
09/17/2017  10:51 AM             1,696 README.md
09/17/2017  10:32 AM                 0 test.txt
               2 File(s)          1,696 bytes
               2 Dir(s)  905,851,092,992 bytes free
C)C:\Projects COE\Hw1\Homework\1>type test.txt
This is some example text for branch test1
C:\Projects COE\Hw1\Homework\1>
  
D) C:\Projects COE\Hw1\Homework\1>git commit -m "added text.txt"
[test1 5f0d128] added text.txt
 1 file changed, 1 insertion(+)
 create mode 100644 Homework/1/test.txt
  
E) No we don't see it because test.txt was made on test1.
C:\Projects COE\Hw1\Homework\1>git checkout test2
Switched to branch 'test2'
D       Homework/test.txt

C:\Projects COE\Hw1\Homework\1>dir
 Volume in drive C is Windows
 Volume Serial Number is 1836-B444

 Directory of C:\Projects COE\Hw1\Homework\1

09/17/2017  11:04 AM    <DIR>          .
09/17/2017  11:04 AM    <DIR>          ..
09/17/2017  10:51 AM             1,696 README.md
               1 File(s)          1,696 bytes
               2 Dir(s)  905,859,334,144 bytes free
  
F)C:\Projects COE\Hw1\Homework\1>dir
 Volume in drive C is Windows
 Volume Serial Number is 1836-B444

 Directory of C:\Projects COE\Hw1\Homework\1

09/17/2017  11:06 AM    <DIR>          .
09/17/2017  11:06 AM    <DIR>          ..
09/17/2017  10:51 AM             1,696 README.md
09/17/2017  11:07 AM                42 test.txt
               2 File(s)          1,738 bytes
               2 Dir(s)  905,858,326,528 bytes free

C:\Projects COE\Hw1\Homework\1>type test.txt
This is some example text for branch test2

G) C:\Projects COE\Hw1\Homework\1>git checkout test1
error: The following untracked working tree files would be overwritten by checkout:

        Homework/1/test.txt
Please move or remove them before you switch branches.
Aborting

C:\Projects COE\Hw1\Homework\1>git add test.txt

C:\Projects COE\Hw1\Homework\1>git commit
Aborting commit due to empty commit message.

C:\Projects COE\Hw1\Homework\1>git commit -m "added text.txt"
[test2 47e5d52] added text.txt
 1 file changed, 1 insertion(+)
 create mode 100644 Homework/1/test.txt

C:\Projects COE\Hw1\Homework\1>git checkout test1
Switched to branch 'test1'
D       Homework/test.txt

H) C:\Projects COE\Hw1\Homework\1>git checkout master
Switched to branch 'master'
D       Homework/test.txt
Your branch is up-to-date with 'origin/master'.

C:\Projects COE\Hw1\Homework\1>git merge test1
Updating 29772fa..5f0d128
Fast-forward
 Homework/1/test.txt | 1 +
 1 file changed, 1 insertion(+)
 create mode 100644 Homework/1/test.txt
 
I) I see test.txt from the test1 branch.
C:\Projects COE\Hw1\Homework\1>dir
 Volume in drive C is Windows
 Volume Serial Number is 1836-B444

 Directory of C:\Projects COE\Hw1\Homework\1

09/17/2017  11:11 AM    <DIR>          .
09/17/2017  11:11 AM    <DIR>          ..
09/17/2017  10:51 AM             1,696 README.md
09/17/2017  11:11 AM                42 test.txt
               2 File(s)          1,738 bytes
               2 Dir(s)  905,858,449,408 bytes free
  
J) There already exist a test.txt on the master branch so we could not merge test2.
C:\Projects COE\Hw1\Homework\1>git merge test2
Auto-merging Homework/1/test.txt
CONFLICT (add/add): Merge conflict in Homework/1/test.txt
Automatic merge failed; fix conflicts and then commit the result.
  
K) C:\Projects COE\Hw1\Homework\1>git checkout test2
error: you need to resolve your current index first
Homework/1/test.txt: needs merge
  
L) C:\Projects COE\Hw1\Homework\1>git status
On branch master
Your branch is ahead of 'origin/master' by 1 commit.
  (use "git push" to publish your local commits)

You have unmerged paths.
  (fix conflicts and run "git commit")
  (use "git merge --abort" to abort the merge)

Unmerged paths:
  (use "git add <file>..." to mark resolution)

        both added:      test.txt

Changes not staged for commit:
  (use "git add/rm <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        deleted:    ../test.txt

no changes added to commit (use "git add" and/or "git commit -a")

M) <<<<<<< HEAD
This is some example text for branch test1
=======
This is some example text for branch test2
>>>>>>> test2
C:\Projects COE\Hw1\Homework\1>type test.txt
This is some example text for after merging

N) C:\Projects COE\Hw1\Homework\1>git status
On branch master
Your branch is ahead of 'origin/master' by 1 commit.
  (use "git push" to publish your local commits)

You have unmerged paths.
  (fix conflicts and run "git commit")
  (use "git merge --abort" to abort the merge)

Unmerged paths:
  (use "git add <file>..." to mark resolution)

        both added:      test.txt

Changes not staged for commit:
  (use "git add/rm <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        deleted:    ../test.txt

no changes added to commit (use "git add" and/or "git commit -a")

C:\Projects COE\Hw1\Homework\1>git add -A

C:\Projects COE\Hw1\Homework\1>git commit -m "merged from test branches"
[master c76c8cb] merged from test branches

C:\Projects COE\Hw1\Homework\1>git checkout test2
Switched to branch 'test2'

O) C:\Projects COE\Hw1\Homework\1>git branch -d test1
error: The branch 'test1' is not fully merged.
If you are sure you want to delete it, run 'git branch -D test1'.

P) C:\Projects COE\Hw1\Homework\1>git checkout master
Switched to branch 'master'
Your branch is ahead of 'origin/master' by 3 commits.
  (use "git push" to publish your local commits)

C:\Projects COE\Hw1\Homework\1>git branch -d test1
Deleted branch test1 (was 5f0d128).

C:\Projects COE\Hw1\Homework\1>git branch
* master
  test2
  
Q) Because master is the branch that I merged into, and we already resolved our merge conflicts on master.

R) C:\Projects COE\Hw1\Homework\1>git checkout test2
Switched to branch 'test2'

C:\Projects COE\Hw1\Homework\1>git branch -d test2
error: Cannot delete branch 'test2' checked out at 'C:/Projects COE/Hw1'

S) C:\Projects COE\Hw1\Homework\1>git checkout master
Switched to branch 'master'
Your branch is ahead of 'origin/master' by 3 commits.
  (use "git push" to publish your local commits)

C:\Projects COE\Hw1\Homework\1>git branch -d test2
Deleted branch test2 (was 47e5d52).

C:\Projects COE\Hw1\Homework\1>git branchf
git: 'branchf' is not a git command. See 'git --help'.

The most similar command is
        branch

C:\Projects COE\Hw1\Homework\1>git branch
* master
