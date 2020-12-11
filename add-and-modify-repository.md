## 學習目標

* 在 Git 中進行合併\(merge\)與分支\(branch\)

## Repository特點

* Git 的 Repository 儲存了歷史紀錄的子數據

* 檔案通常隱藏在主目錄中的.git資料夾

* 隱藏的資料夾\(.開頭\)常存放使用者不需直接接觸的檔案

* `ls -a` // 能顯示被隱藏的檔案

## Repository概念圖

![](https://lh5.googleusercontent.com/eNxEkglDrP44rLeAzDOGNGUJudd8bpScXKaD3vFS60-QT0AbGNNpf_ZUitPaHNypVqaov8kVx6-Xbhz4Zg72n_ESDyFn6Brxr2DGFHsZPEirpOtK3iL-s01lon7fMQRE4YmrG5_a)

## 狀態\(Stage\)

提交檔案到repository有兩種方法：

* ~~一種是直接從Working directory直接commit\(?\)~~\(更新：不可這樣操作\)
* 另一種是先儲存到Staging area

![](https://lh3.googleusercontent.com/pHSYhUYk7fRCOer9lWd-GLLSF0JDFfym3nFt5FRNCpmupR-Zqcaz5sgO9LVyScrH_b96HrzxdXCjgeKgH8cK1AXCV6bPksp6kh9weHv36kT7OPNK-cwq1M7CFkzjPtaFTsNhJTUS)整理：（註：由於markdown不支援跨欄位的表格，因此這邊放圖片）![](/assets/20170621 025635.png)註：參數差別 \(O代表會被還原到HEAD\)

|  | working directory | staging area | repository |
| :--- | :--- | :--- | :--- |
| -soft |  |  | O |
| -mixed |  | O | O |
| -hard | O | O | O |

* 注意：選取檔案時一定要加副檔名

* 參考：[如何將檔案從stage移除? \| 點燈坊](http://oomusou.io/git/git-remove-stage/)

## Git diff 檔案的差異

![](https://lh3.googleusercontent.com/9ElMpv7vsXySpPGtEYfdmAcW0XP-CuYyPC6gn0erdnfaKvyVhKU6H1PZflSjZipfc4sLVTLkV6heeMUzvgu0XBusiYxJ65nYWQ9V9xzvY6R-2aZpYoOFUqc1y0jyvCL4RUnHcnqm)

* 注意第二題：`git diff --staged`比較的是staging area跟Repository最新的commit\(commit1\)

## 編寫提交訊息

* 一般而言commit後會跳出記事本編輯，但也可以用下面的快速編寫方法

* `git commit -m “<Commit_message>”` // 別忘記雙引號

* 建議使用祈使句\(如用change，而不要用changes,changed\)

* [訊息樣式指南](https://gdgdocs.org/document/d/1HZ9Bo1mDKhe3JZzmFvekL5P2WHafpCaEXTymj__FUYw/pub?embedded=true)

## 分支\(Branch\)

## ![](https://lh3.googleusercontent.com/X-bIi4XW8T8XDTMIqZqlOaUIhDIpdb2mFYbey_qdvrMlqM1u1gbl015e4h_6N9dY46O9AGG3az4eGuUeTeNTw8AbGAZ8s5xGYnlKFfviEK0y0o1eHInnolVNc8GlHFpKcfwx7wFv)

* 用途：

  * 添加不同語言版本時

  * 區分stable,beta,dev version

* 橘色代表branch name

* `git branch` // 顯示當前的分支

* 註：~~tip\(頂點/端\)~~指向編輯中\(當前\)的分支\(更正：應為HEAD\)，以星號\(\*\)表示

  * tip\(頂點\)：last commit or most recent commit on a branch

  * 來源：[What is a branch tip in Git? - Stack Overflow](https://stackoverflow.com/questions/16080342/what-is-a-branch-tip-in-git)

* master：預設的分支名稱

* `git branch <branch_name>` // 新增一個指定參數的分支

  * 如：`git branch easy_mode` // 新增名為easy\_mode的分支

* `git checkout <branch_name>` // 切換到指定參數的分支

## 用分支協作

* remote branch：不是自己建立的branch

* `git log --graph --oneline <branch1> <branch2>`

* * `--oneline` // 輸出成一行以便閱讀
* 如：`git log --graph --oneline master coins`

![](https://lh3.googleusercontent.com/pCio_j-AE8yyd3OkY9yNEZy4Wm5EreZZX68ovSDHZcrh1pbbv03_UAkkH9awYdv2GPWI328ZD87q00dp_Y-zTRhgeoRxOaG6jzTOPvKECuOQVjQhWCteOaFlV4Da14x-xJWv9Xq7)

* 上：coins分支創建後，向master分支中添加的commit

* 中：向coins分支中添加的commit

* 下：在coins分支創建前存在的commit

## 可訪問性\(Reachbility\)

![](https://lh4.googleusercontent.com/CjtNkkhrEKfBIIN6SE1_RDnaSGf7SrHM5ZJpcWK9SFTKmheT8wEr_gY1I1h11RH32Jur9invR9_DdViMREuutei9K62lz8cjK9c7GcOQXZTCo8TnhwH1Ek18ELNPIYwi60V_5QZg)

* git log不會顯示所有commit，只會往回追溯parent，而每個commit都知道他的parent

* 注意：從新到舊的commit

## 分離的HEAD

![](https://lh6.googleusercontent.com/E7z1orgF9xSrzquabdiPRH1Yk5obw-bYl8DiF_mdbxsw4XhlQU5j0k2yf8d1bYYysKCutTxtTrOyzJ4m3jTSJryA-zyZcaSOkwlWg98YxhWzo7NJj3FLcWV3hnnWfwAWS6du2f5d)

* HEAD：當前\(現在正在編輯\)的commit \(圖中以藍色星號表示\)

* 若checkout到animation，並新增一個commit到animation，再checkout到master，剛剛新增的commit會丟失，除非記下commit ID，否則無法透過git log到剛剛新增的commit

* `git checkout -b <new_branch_name>` // 新增一個分支，並指向它

  * 相當於執行下面兩行命令：

  * `git branch <new_branch_name>`

  * `git checkout <new_branch_name>`

* 下圖為執行命令後結果：

![](https://lh4.googleusercontent.com/StOIyU7yRKmKMdhgU1GxS9PkEkcPzge3u8qunLzuviuGclXWbjx_pjEqI6-_hjG43RcKqc_rcaO6BmoLTm2cOO7IdCiijqrV-ptVwPp174R82zK1hyRXyoQAvmvvj-UeVuZfpMuA)

若把這個動作形象化，可以分成兩種情況：

* 在夢中擁有時光機：\(分離的HEAD\)  
  回到過去指定的時間點，汙染世界破壞了地球，但由於是夢，一覺醒來後對現實生活\(master\)並沒有什麼影響

* 在現實中擁有時光機：\(新建一個branch\)  
  做了一件極為後悔的事，因此回到做決定前的時間點，並重做一次正確的決定\(new branch\)，之後一直過著正確決定的生活\(checkout到此branch\)

## 合併\(Mege\)

| without original file | with original file |
| :--- | :--- |
| ![](https://lh4.googleusercontent.com/Iw5qJH8zmZKasOo0sMZ-i-Me0MGaWmXO9AVjMYOJdiC4nu9R_hJtMDn2bdCszecQXUABygQyocMDnP_jHeP1IkLpASd1qyw4fHeyM-HvqkDfQogHv4DzxKVj6-47_a8ja7_JVG0e) | ![](https://lh3.googleusercontent.com/6sE4xz_YNQwQ3tgvYLnLuArgb56K3aiiJagtRDABnD_nuPBFO_wTAiUP4DT84gtRwy2g-a_vEwWMSt_c1LUG9D7KwaPQod622q9E54XvqCOQ3F-9G12gHI3x4t_PNmhDS4JHZURB) |
| 注意：當合併時，雙邊都有的部分會包含在最終版\(yes\)，只有單邊有的部分為unknown需再決定，雙邊都沒有的部分則為no | 說明在下 |

with original file:

| original | Jake | Rachel | In final? | 備註 |
| :--- | :--- | :--- | :--- | :--- |
| yes | yes | yes | yes | 如B,D |
| yes | yes | no | no | 如A |
| no | yes | no | yes | 如C,E |

\*上表Jake與Rachel可對調

* A可想成建造公共建設，一開始政府說要建，但只要有一人反對就不蓋

* C,E可想成沒有主見/人云亦云的人，一開始說不要，但只要有人說要還是會照做

## 將Coins Branch合併入Master Branch

![](https://lh5.googleusercontent.com/Sei00Yj1KylkFq16R6rc_A4L-sZE9kC_KmL67o6pRO-Bk1iXTXfR5otzfIx-iRykF-qkcDCQM-iJId34hgce1fWj1ivHdovj5VAxO0sN6nacgnbp88xNsl72QS1TinWSm_TCr5o1)

* 將Coins Branch併入Master Branch並不等同於在Master Branch內新增一個包含Coins Branch最新版\(ships on coins\)的commit，後者僅包含Coins Branch的內容

* 由於Coins Branch已經併入Master Branch，因此不再需要所以可刪除Coins Branch，請注意刪除分支代表移除標籤\(label\)，歷史紀錄中的commit還在；但若沒有分支能指向commit，則等同於拋棄commits

![](https://lh5.googleusercontent.com/sOO-Zks28-fLUettDG93YDJeBRBg54_Un-S3v9Ha7alxd_CJPLLl6qpZfWZi4hTAvwZFlQUF6lzO2kGq4Hvrj-8BTeq9A3nkpvwUuCe3cq5x__H_xiEQ-4aIgI4enyD8mZNPYHrx)

* 注意紅框處，合併後Coins Branch依然會顯示在Master的Git log輸出中，輸出結果由時間排序，因此兩個Branch的Commit可能會交錯出現\(如下表\)

| timestamp\(假設\) | branch name | commit name |
| :--- | :--- | :--- |
| 12:00 | coins | first coins commit |
| 13:00 | master | fix screen typo |
| 14:00 | conis | helper fns |

## 通過命令行合併

* 因為合併後的Branch的git log由時間排序，因此不同Branch間可能交錯排序，因此第n個與第n-1個commit原先可能不是同個branch，因此需要git show來比較它的parent

* `git show <commit_id>` // 比較此commit\(通常含有bug\)跟parent的差異  
  等同於 `git diff <commit_id> <commit_parent_id>`

* `git branch -d <branch_name>` // 刪除指定branch的標籤\(label\) \(注意：並非commit，因此還是可以透過ID找回\)

合併branch1與branch2

* `git checkout branch1` // 先切換到branch1

* `git merge branch2` // 再合併branch2

  * 也可輸入`git merge branch1 branch2` // 非必要，僅能幫助知道合併的對象

  * 由於只有兩個分支，合併的前後順序並不重要

合併master與coins

![](https://lh5.googleusercontent.com/mHRJuaVNfVojMqPLOJpEkeVjKp_TB6zjcgTlIDZkFYiA3nP-NgopomXnRmjgcgBBm5Qr6Q8j16fZetUkoXIwhvF1nlivNUhqv1f_mrtsB7LzqllsutAvudiT5fhRviGBqALI2_4I)

合併時發生錯誤，因為文件的狀態不同於講者，因此需要做以下的更改：

* `git merge --abort` // 將文件恢復到還沒合併前的狀態

* 在game.js的第424行新增`this.delayBeforeBullet = 10;`

* 編輯完成後提交一個新的commit

## 切換Branch的Error

```
lin@minidinos-ThinkPad-L460 MINGW64 /C/Users/lin/GD/1.Class/1.code/how-to-use-git-and-github/asteroids (master|MERGING)
$ git checkout easy_mode
game.js: needs merge
error: you need to resolve your current index first
```

由於Merge時有Conflict沒有排除，因此有[兩個方向可以排錯](https://goo.gl/jmHWaB)：

* 解決conflict後再次執行merge

* 將文件恢復到merge前的狀態

  * `git reset --merge`

  * `git merge --abort` // 新語法，[git v1.7.4 開始支援](https://goo.gl/4avGDt)

## 合併衝突

![](https://lh5.googleusercontent.com/BjbATGCBVYPzo42_W0yvP0Se4Ixo871DreToTiak_uGbK3XzajkVd7w2fIpgIj5neR0qkNcfJCoK3rs-is5OpodgejaiyUjaMk_4kUA1C9hUCfJ507ZYs74r0-Oe7V7JKnIoihZ1)

由於不知道要保存B或B’還是B’’，因此三者皆為unknown

## 合併衝突檢測

有兩種情況

| 上面是相同的，但下面是由兩位不同的作者撰寫，有著不同的功能 | 上面也都是相同的，但下面雖然有著相同的功能，卻用不同的（實施）方法\(implement\)寫，因此要針對情況選擇適合的方法 |
| :--- | :--- |
| ![](https://lh3.googleusercontent.com/jdOJY5xuWD5xUF9qRqYOt_kxInczCdq1c3-OB3LZCb6wWXXXO3XknWJBLiK_RbDNZjapBr73hXLpJIFyuCDR1QCVdYZaj9bo_JkFqiqJyGdHwynIMmNBDxNDwqmK1dcRmXLFg_Qb) | ![](https://lh3.googleusercontent.com/_OemxfQqVskIqIElserVLdWxvCp8f1hRvynr26NiYdusUb_slJyWPOMK_ui-X1ARnO8gYTTE7Ni6twP5a_ZoWfo8_GWQcvWxBmrAR-jyUl80Ytu0AFUCxre21x-mW0tz__ahvMMI) |

但除非利用人工智慧，否則機器沒有聰明到自動幫你選擇要保留哪個，因此若有合併衝突，Git會詢問你要保留哪個檔案。

## 更新Easy Mode分支

將Master Branch合併到Easy Mode Branch

| Before | After |
| :--- | :--- |
| ![](https://lh6.googleusercontent.com/jWEXzWsk1dZVYgw5rU3X4shBGUCJsn32JzGePKN8U3ihzFXPZ9uUeRYCkPFfBwZDtoP8avUlsAsvWAxHV4aHLU5Xj-jQjCO3ZibAi13veYH10EfTjRi0GMTW1obo8uTqinR0Vj2X) | ![](https://lh6.googleusercontent.com/3cy2MS9sFYeWs8SzCX6ZbygkEbi7efHE2hporQOuzqxCMVZOa66auyBI85nOPuaO6STpzmoIv_2HyQcLT9WFfEFMnkrxqf7-aCv0C32k9xV9UNwKkN4P8ie44gTHR9Hh4Rmj39PT) |
|  | 註：新增一個節點，使它同時有兩個parent\(master, easy-mode\)，並將easy-mode的標籤移到新建的節點上 |

---

## 常用指令整理

* `ls -a` 能顯示被隱藏的檔案

* Working Directory → Staging Area

  * `git add <file_name>` 新增

  * `git reset <file_name>` 移除（註：詳細參數在上面內文）

* Staging Area → Repository

  * `git commit <file_name>` 提交

* `git diff --staged` 比較 staging area 與 HEAD

* `git commit -m “<Commit_message>”` 編寫提交訊息

* `git branch` 顯示當前的分支

  * `git branch <branch_name>` 新增此分支

  * `git branch -d <branch_name>` 刪除指定branch的標籤\(label\)

* `git checkout <branch_name>` 切換到此分支

* `git log --graph --oneline <branch1> <branch2>` 以圖形輸出成一行一行

* `git checkout -b <new_branch_name>` 新增一個分支，並指向它（等同下面兩行）

  * `git branch <new_branch_name>`

  * `git checkout <new_branch_name>`

* `git show <commit_id>`  比較此commit\(通常含有bug\)跟parent的差異

  * 等同於`git diff <commit_id><commit_parent_id>`

* 將文件恢復到merge前的狀態

  * `git reset --merge`

  * `git merge --abort` 新語法，[git v1.7.4 開始支援](https://goo.gl/4avGDt)

* `git init` 以問答的方式建立package.json

* `git status`  顯示最後提交更改的文件

## Git Bash中路徑問題

* 原本存放檔案的位址：`C:\Users\lin\GD\1.Class\1.code`

* 如果直接輸入 `cd C:\Users\lin\GD\1.Class\1.code` ，會跳出`No such file or directory`

* 後來在stackoverflow上找到[這篇](https://stackoverflow.com/questions/11617433/git-bash-questions)，解決了我的問題：

* 1. 將C:\改成/C/

  2. 將\改成/

  3. 上面地址會變成`/C/Users/lin/GD/1.Class/1.code`

## head v.s. HEAD v.s. branch tip\(頂點\)

* head\(小寫\)：在Repository內所有的commit

* HEAD\(大寫\)：在Repository內最新的commit

* branch tip\(頂點\)：所有Branch內最新的commit

* 參考資料：[What is HEAD in Git? - Stack Overflow](https://stackoverflow.com/a/4381549)

* 參考資料：[What is a branch tip in Git? - Stack Overflow](https://stackoverflow.com/questions/16080342/what-is-a-branch-tip-in-git)

## 推薦的線上繪圖工具

* [gliffy](https://www.gliffy.com/)

* [yUML](http://yuml.me/diagram/activity/draw)



