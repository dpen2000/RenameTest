This repository tests out two scenarios of renaming and editing files in the same commit in git. 

It is intended to demonstrate that file rename detection works in git without using ``git mv`` and specifically that a file can be modified in the same commit without using ``git mv`` (see branch at https://github.com/dpen2000/RenameTest/tree/ManualRenameWithOneParagraphRemoved ). 

It also demonstates that using ``git mv`` and editing the file too substantially in a commit doesn't guarantee rename detection because ``git mv`` was used (see branch at https://github.com/dpen2000/RenameTest/tree/GitMvWithThreeParagraphsRemoved ).

Each branch linked above contains a README.md showing exact steps followed (With the caveat that when I created GitMvWithThreeParagraphsRemoved branch, I had readme file in my working copy and didn't show ``git status`` lines concerning this). I also apologize for my awful to rename file to ``anoldstory.txt`` with horrendous lack of casing :-D
