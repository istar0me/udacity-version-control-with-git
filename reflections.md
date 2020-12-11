## 實作

我利用課程中所學到的方法與指令，Fork原作的[Recipe](https://github.com/LarryMad/recipes)到我的帳號底下，再Push本機端的檔案到GitHub上

[istar0me/recipes  
｜GitHub](https://github.com/istar0me/recipes)

而以下的檔案是課堂中老師提出的問題沉思，我把問題用純文字\(Plaintext\)打起來，儲存起來Push到GitHub上

[istar0me/Reflections  
｜GitHub](https://github.com/istar0me/Reflections)

## Lesson 1

```
How did viewing a diff between two versions of a file help you see the bug that
was introduced?

    不用一行一行慢慢確認，相同的部分不會列出，只會列出不同的部分，因此可以專注在不同的部分

How could having easy access to the entire history of a file make you a more
efficient programmer in the long term?

    可以專注在編寫程式，不用特別記更動哪些部分

What do you think are the pros and cons of manually choosing when to create a
commit, like you do in Git, vs having versions automatically saved, like Google
docs does?

    manually saved
    pros:較易分辨各版本間差異
    cons:意外時資料可能遺失

    automatically save
    pros:不會忘記要儲存
    cons:磁碟頻繁讀寫、每個版本不是剛好一個段落，較難管理

Why do you think some version control systems, like Git, allow saving multiple
files in one commit, while others, like Google Docs, treat each file separately?

    能同時多工儲存，更有效率。

How can you use the commands git log and git diff to view the history of files?

    git log // 直接顯示所有的commit內容
    git diff <file_1> <file_2> // 比較檔案1跟檔案2

How might using version control make you more confident to make changes that
could break something?

    即使弄錯了，只要回到指定的版本就可以了
```

## Lesson 2

```
What happens when you initialize a repository? Why do you need to do it?

    新增一個.git的資料夾，供git儲存與辨識相關檔案

How is the staging area different from the working directory and the repository?
What value do you think it offers?

    working directory:電腦上看見的目錄
    stagina area:目錄與儲藏室的中繼站
    repository:儲藏室

    value:中繼站可以充當緩衝區，若有錯誤可以先更改

How can you use the staging area to make sure you have one commit per logical
change?

    每次邏輯更改時都要git commit

What are some situations when branches would be helpful in keeping your history
organized? How would branches help?

    1.新增實驗版或新語言時
    2.使用分支不會影響主線(master)的內容

How do the diagrams help you visualize the branch structure?

    能直觀地看出前後順序
```

## Lesson 3

```
When would you want to use a remote repository rather than keeping all your work
local?

    When I want to collaborate with someone else, it would be a great method.

Why might you want to always pull changes manually rather than having Git
automatically stay up-to-date with your remote repository?

    Because if it pull automatically, I can recognize what the differences between the two versions.
    So I prefer to update manually to ensure all changes are logic-based.

Describe the differences between forks, clones, and branches.  When would you
use one instead of another?

    forks:
        說明：等同於先clone到本機端，再push到remote repository上，但這個步驟由GitHub伺服器代勞
        註：fork此詞由GitHub發明，因此專指GitHub內從事的行為，本機端的操作並不包含在此範疇
        時機：有好的open-source專案，但有些地方不符合自己的胃口，因此想做些更改
    clones:
        說明：複製Remote repository到本機端，或從本機端複製一份副本到本機端
        時機：想研究別人的代碼時(?)
    branches:
        說明：在主線上新增支線，避免更動主線的檔案
        時機：適合用於添加一些新功能(如支援新的語言)等
```

\*註：本頁面只放有解出來的問題，未解的問題在GitHub原始檔上

