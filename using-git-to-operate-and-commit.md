# 教材

本文主要參考

* [How to Use Version Control in Git & GitHub \| Udacity](https://www.udacity.com/course/how-to-use-git-and-github--ud775)
* [簡介 · Git](https://zlargon.gitbooks.io/git-tutorial/content/)
* [用Git版本控制【Git的基本介紹】 \| 連猴子都能懂的Git入門指南 \| 貝格樂（Backlog）](https://backlogtool.com/git-guide/tw/intro/intro1_1.html)
* [Git 教學\(1\) : Git 的基本使用 - 好麻煩部落格](http://gogojimmy.net/2012/01/17/how-to-use-git-1-git-basic/) // 推薦閱讀

## 比較兩文件

![](https://lh3.googleusercontent.com/Ff2gDM9WAP3_p4vfWPrApj42mE2YkhG6CUj2kzRq2P5aNm9MZA4UJWoC4ll1-xbAwi-BbBftAODmKea9taJ-wRFMbe0cFQtd6isnxkKr-EI4gADrNtvwMWzkPdBrk13dHXn54pr6)

* `fc <file_1><file_2>` // windows
* `diff -u <file_1><file_2>` // Mac OS or Linux

## 儲存檔案的時機與大小

![](https://lh6.googleusercontent.com/ZkF9w0kLiI3yFUto1xAHQdF5MqzNTmrd9tVuPtpHgszGvjvZJP4RZvecJqpp_LHctEVkPsUy2msIqyG-eMGYGNJoMNTQlGQdSUKVuUJW8se0fcWIvpnSgHruK5YdxjZKA2bgvFoo)

![](https://lh6.googleusercontent.com/U8xhQtqheUZamzt1qYaFka5JI1OqLNNP7bnp2mBw4LuGEeucdrP9oASCC6IVIHyBKCb_pl3zLKh4ej3HbjbnP6H_LnApTlvDgNo97WvtqKiREx9xQm3JSGuWKdaelqFVGNccRofD)

* 每次進行邏輯更改時儲存檔案\(建議手動非自動\)

## 版本控制系統：CVS v.s. SVN

* CVS, Concurrent Version System：協作版本系統
* SVN, Subversion：子版本
  * 可視為CVS的升級版
  * 特點：中央控管(修改完要submit回一個中央系統)
* Mercurial \(abbr:hg\)
  * 性質類似於git
* 參考資料：[為什麼比 GIT 更好－－理解 Mercurial 版本管理系統 - OpenFoundry](https://www.openfoundry.org/tw/foss-forum/9266-why-git-better)

## 概念圖

## ![](https://lh6.googleusercontent.com/3By9aYs4duUaLGoHQDZedC-rQndys9a-Jb7W7lygh5Umjui_Rc5IfINRtea56W6NA2WH42XLgRbKuzNbp6SnGPBX2nnvFQebWIl929MHfFg9LlrWLusVJo1H-0_Hf5JodokyEgq_)

## ![](https://lh3.googleusercontent.com/q5ODfpmdWEJgkcWj822KtfRNBKHSMxVguC1EP8wA5TK5BYHLYqbt1G8umNN3jg8P6jsz763otmJZfI8SFYKgt3ddeF11NyN3NQ_lePqXu9vA69a7Jry_drnOdPAPMGiwq-8GyR8Z)

* \(完整版可參考第三章\)

## 同時提交多個git文件

![](https://lh5.googleusercontent.com/KwIcYPLrNN-QsbhhtscNIuCEAbacw5IlbdlBMjT8rkJ4A0CGYk1x-_aD4A4TwybKNaq_3dlj5UywwDA1XAKnm546ZxuaztLNa1HubIy4CFEnAP-XcyYxPqlXHoK1WCiuMF5kuaDx)

* repository\(儲藏庫\)：放置git文件的倉庫
* `git log --stat` // 顯示統計數據\(如幾個檔案變更，新增多少內容\)
  * 在此模式下，可以按Q停止查看輸出

## 設置\(教學中建議的\)工作環境\(Windows\)

![](https://lh6.googleusercontent.com/c48EuS4SiU1u9gdNMsNNk7MSmIiVKlOV_BGiHz9DINdeaFxcYSaXpNYes0CloUtPUpSEPmnOZ6D7IzZ8GtPKYQ65vJAkZ6g8QSpYbgc4D1nmhlDPQ6geZiSDH37RjW86Hw1clC7D)

* 瀏覽器會預設儲存成txt，這點要特別注意
* 可用`mv git-completion.bash.txt git-completion.bash`
* `git config --global core.editor "'<text_editor_path>' -n -w"` // 設定預設編輯器
  * `-n`在新視窗中開啟
  * `-w` 關閉文字編輯器後再繼續
  * 不明原因設置失敗，論壇上有人有[相同問題](http://discussions.youdaxue.com/t/git-bash-sublime/39610)
* `git config --global push.default upstream` // 建議用法，未解釋
* `git config --global merge.conflictstyle diff3` // 建議用法，未解釋

---

## 常用指令整理

* `git commit` 提交
  * `git commit --amend` 更動最後一次提交
  * `git log` 顯示所有commit內容\(歷史紀錄\)
* `git status` 查看目前這個Repository的檔案狀態
* `git config --list` 查看自己的設定值
  * `git config --global core.editor [***]` 指定編輯器為***
* `git diff <commit id_1> <commit id_2>` 類似於fc或diff
* `git --version` 可查看git的版本
* `git help <command>` 有問題時可用此指令獲得幫助\(如：git help diff\)
* `git clone <repository_url>` 複製repository到當前資料夾
  * `https://git.gitbook.com/YOUR-USER-NAME/YOUR-BOOK-NAME.git` GitBook 的 Git 檔案網址(需登入)
* `git config --global color.ui auto` 獲得彩色的輸出
* `git checkout <commit id>` 恢復到之前的版本
  * \(註：不等於svn checkout\)
  * 註：若用git checkout還原到舊版本，則用git log輸出歷史紀錄時會發現最新的commit是剛剛還原的版本，但這會有’detached HEAD'的問題
  * ~~"好像"可以不用打完整的commit id，可以只打最前面的部分即可~~
  * \(更新：至少要打前四碼，前提：前面部分commit id沒有衝突\)
  * 如：完整的id為7c81b8021ec16c5c7b240220314d01200957d605，可以只打7c81b8
* `git rm -f [filename]` 移除filename的暫存，並把它刪除
* `git rm --cached [filename]` 移除filename的暫存，成為未追蹤，但不刪除。
* `git mv a b` = mv a b + git rm a + git add b
* `git commit --amend` 更動最後一次提交
* `ls -a` 顯示隱藏檔 \(以".”開頭的檔案\)
* `mv <file_initial_location> <file_destination_file>` 移動檔案或重新命名
* `history` 可用來查看輸入過的指令
## git bash 執行緩慢問題

[Git/Bash is extremely slow in Windows 7 x64 - Stack Overflow          
](https://stackoverflow.com/questions/4485059/git-bash-is-extremely-slow-in-windows-7-x64)測試過，重開機後已解決效能差的問題

## Git 錯誤和警告解決方案

1. Should not be doing an octopus（不應執行 octopus）  
   Octopus 是 Git 用來合併多個不同代碼版本的一種策略。如果在不合適的情況下嘗試使用該策略，則可能會出現此消息。

2. You are in 'detached HEAD' state（你處於「分離的 HEAD」狀態）  
   Git 將你目前所在的提交稱為 HEAD。可通過切換到前一個提交來「分離」HEAD，這在下一個影片中有說明。雖然此警告聽起來不太好，但分離 HEAD 實際上不是壞事。Git 只是向你發出警告，以便你知道自己正在這樣做。

3. Panic! \(the 'impossible' happened\)（（天哪！「不可能的事」發生了））  
   這是真正的錯誤消息，但它不是由 Git 輸出的，而是由 GHC（編程語言 Haskell 的編譯器）輸出的。它僅在發生特別讓人驚訝的錯誤時才會出現！

![](https://lh3.googleusercontent.com/0s-pk7We5hJNe3x1DSlgEsAUEcbBreSLeqKofki3CQwVWce5RpU_ZPlwWQ4ESvVUs7bZuZqA-5bSaRO9FaQogNn8NyTtSk0qfXfRMTIf1bmjctGiY3Yuhg3g5yK48g_wYsq4J_vo)

* 星號\(\*\)代表有修改尚未儲存



