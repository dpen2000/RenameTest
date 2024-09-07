So in this test, I will rename the file without using ``git mv`` and then I will change the renamed file by removing the last of four paragraphs. I expect that git will detect this as rename after the rename and after the content of the file is changed (because it will still be substantially the same file content)

1. Run ``mv dracula.txt anoldstory.txt``
2. ``git status`` shows
```
On branch ManualRenameWithOneParagraphRemoved
Changes not staged for commit:
  (use "git add/rm <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        deleted:    dracula.txt

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        anoldstory.txt

no changes added to commit (use "git add" and/or "git commit -a")
```
The rename is not yet detected because we haven't added the files into git index yet.

3. Run ``git add anoldstory.txt`` and ``git add dracula.txt``
4. ``git status`` now shows
```
On branch ManualRenameWithOneParagraphRemoved
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        renamed:    dracula.txt -> anoldstory.txt
```
Git has detected the file as renamed despite us not using ``git mv``.

5. Edit the file to remove the last paragraph and then run ``git add anoldstory.txt``
6. ``git status`` now shows
```
On branch ManualRenameWithOneParagraphRemoved
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        renamed:    dracula.txt -> anoldstory.txt
```
This is identical to step 4 as the rename is still detected despite not using ``git mv`` and making a small change to the file.

7. Run ``git commit -m "Manual rename file with one paragraph removed"``
```
[ManualRenameWithOneParagraphRemoved 2cf6f2f] Manual rename file with one paragraph removed
 1 file changed, 1 insertion(+), 3 deletions(-)
 rename dracula.txt => anoldstory.txt (74%)
```
The output here shows the rename detection in action showing that the ``anoldstory.txt`` is 74% similar to ``dracula.txt``

8. Once pushed to GitHub, visit https://github.com/dpen2000/RenameTest/commits/ManualRenameWithOneParagraphRemoved/anoldstory.txt
9. Note that this page shows ``Renamed from dracula.txt
(Browse History)`` and clicking ``(Browse History)`` link shows the original commit in ``main`` where file called ``dracula.txt`` was created.
