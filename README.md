So I am going to rename dracula.txt with git mv and then remove three of the four paragraphs and then commit.
I expect that despite the git mv usage, git and GitHub will still not recognise the renamed and changed file as a rename.

So steps are:
1. ``git mv dracula.txt anoldstory.txt``
2. ``git status`` shows:

```
On branch GitMvWithThreeParagraphsRemoved
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        renamed:    dracula.txt -> anoldstory.txt
```

3. Edit file to remove last 3 (of 4) paragraphs.
4. Looking at ``git status`` now:
```
On branch GitMvWithThreeParagraphsRemoved
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        renamed:    dracula.txt -> anoldstory.txt

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   anoldstory.txt
```
5. Run ``git add anoldstory.txt`` to add the changes into the git index.
6. ``git status`` now shows:
```
On branch GitMvWithThreeParagraphsRemoved
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   anoldstory.txt
        deleted:    dracula.txt
```
Even here we see that using "git mv" hasn't worked if we expect it to allow a file to be modified in the same commit and still show as renamed if file changes too much. This is because git detects renames based off a new file being similar enough to a deleted file, not off "git mv" usage.

7. Push branch to github
8. Go to history of the renamed file:
https://github.com/dpen2000/RenameTest/commits/GitMvWithThreeParagraphsRemoved/anoldstory.txt
9. Observe there is no link at bottom of the page allowing the user to browse the history of the file with it's old name.
