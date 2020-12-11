## 前言

雖然官方已經有了[說明手冊](https://guides.github.com/activities/hello-world/)，但它主要是在講解概念，並沒有教學如何在Git\(或終端機\)上操作，由於筆者所用的Heroku\(雲端運算平台\)也是使用Git版本控制系統，因此打算從終端機打指令下手，真正瞭解如何實作。

## 什麼是GitHub？

* GitHub：線上Repository託管平臺

* 能夠貢獻\(Contribute\)自己的內容

* 許多\(注意:並非全部\)都是開源的，代表可以自行修改成想要用的

* GitHub鼓勵大家託管公開的Repository，並藉由託管私人的Repository收費

## [幫我記住使用者名稱和密碼](https://help.github.com/articles/caching-your-github-password-in-git/)

有三種方法

* Repository若使用[SSH](https://help.github.com/articles/connecting-to-github-with-ssh/)，則必須用SSH認證而非使用者名稱和密碼，因為較複雜這邊省略

* 使用GitHub Desktop客戶端程式

* 在終端機內輸入`git config --global credential.helper wincred`，會記住憑證

## 使Repository保持同步

![](https://lh4.googleusercontent.com/pUUzsIsJeNDOkSSBmTzewNpu0Jo-jHewXxs8quIuRSvU6WA0KvxfBpTCemeL3bm9mAusqg-c9rTowSDnZd-NwrW91PR0iNP3CvtjRhZCsHygJEz5Y0JT8HJ4ySrVJkxsvJx8-VJG)

* 要先將內容staged跟commit才能提交到GitHub上

* 上圖GitHub那並沒有畫Working directory跟Staging area，雖然它們兩者實際存在於伺服器上，但並不能直接存取，因此省略

* 有別於一般的雲端託管版本服務不同，使用GitHub需選擇兩個版本，When\(時間\) and How\(方式\) to sync?

* 雖然可以直接Clone下來\(GitHub→本機端\)，但不能直接Clone過去\(本機端→GitHub\)，因此需要先新增一個空的Repository再Push

## 遠端代碼庫\(Remote Repository\)

![](https://lh6.googleusercontent.com/2CbF9zLfEGvgGRqEDu5I7ZKPqbqU_Hs0TrhI9UiXA0Wbg0atmvkGfxRTjaQhHLMK6yXgvR1LfqLhPo4HeYBIHrvJQWIG7qlMlLYQFodN2-9Jr-t44wGshZjU5n43sPLBIbgsOR0M)

* 目的：在兩個Repository間同步數據

* 通常不會同步一個commit，而是指定一個Branch，因為一個一個commit傳效率太低

* 由於Master的Tip能觸及全部的commit，因此所有的分支都會出現\(註:承接上次的檔案\)

![](https://lh3.googleusercontent.com/7H_9FfjoffRhn18eYY0tM-F64-ws-iZBj8kmiEO2giYgniwtgLWU23tpd5AY-3kF0ZHhr0bVZnbV4tn_Hq2HXyPilODJ9pUOJyvbpLrspeyZwNNrA2xzj92pwU_7DaGfz3y_wOgK)

* GitHub會由Tip向前追蹤\(e53→fd2→a3b\)

* 由於a3b已經存在於GitHub的伺服器，不須重新上傳，因此上圖不需要選a3b

## 練習新增Repository

![](https://lh3.googleusercontent.com/boaClpDX6eUlaim9779Zw2RkMyCEDieCy4Mt1WIQHTrYCcnbrxfO_zA0eA4K8UtPo4VCNedCBy7aB2uhCvUf1HWNuyjIon46MHKMoVAY3lh6vAA4uQebZeyecSV_y0YbpUXGsW-4)

* 因為我們本機端已經有檔案與commit，因此上圖的「Initialize this repository with a README」不必勾選。

* 註：勾選後會自動產生一個commit（請注意，Git無法Clone沒有Git的Repository），並新增一個空白的README檔案

* `git remote` // 查看目前所有的Remote Repository

* `git remote add <repository_name> <url>` // 新增一個Remote Repository

  * 可以取任何name，name是用來代稱Remote Repository

  * 但如果只有一個Remote Repository，name通常會使用origin

  * url建議採用https，若要採用SSH可參考[這篇](https://help.github.com/articles/connecting-to-github-with-ssh/)

為了確認URL無誤，可以輸入下面這個語法驗證：

* `git remote -v` // v:verbose\(詳細的\)，會輸出更詳細的訊息

* `git push <repository_name> <branch_name>` // 傳送

![](https://lh4.googleusercontent.com/f-t6tiKeukHiW9XPMYYKe8AO878CgN5r8yHzNg5p69Dkq0hDO90oi-machBk8ZJKYHpkDbY_y9y6-U9rsuzFClhOIZ9dR-7XAJvgAhVCsAFNIuH0bQriVbjArhj_5gjXSeo1uuWg)

* `git pull <repository_name> <branch_name>` // 拉回

![](https://lh4.googleusercontent.com/_3FhcmbIhHTEFbHDE2-qoI1_LM4FReYwfGM3GdidiJZu4HZEO5WjsBNe4pUqbKhZGU9H93DWCTIhOxKOCPDV7ZtZltBCcG6rvRLDIlHK9fDXvz9VwcriH51M0vcR9IVOWG8mrMai)

註：上圖問的是只在對Repository進行Push與Pull動作後的狀態，因此本機端與遠端應有同樣的檔案，因此選第三個Neither

## 概念圖

![](https://lh5.googleusercontent.com/T53ElASrFpsKr3GGxjx6YgPwlm1xS1PRyz2ooYIDoLwVELgIJIrssoendkoKnt_AR2ymBd7C1GwoD0Q1XMExjI7F0j-UuTGyAQT15WIK9WdlnDMVdj9H2rFiySpCCpYOl2hyaqxU)

## Fork Repository

| Before![](https://lh6.googleusercontent.com/ikSSVZ_nRzg08-P4UC8YHhf_jzM9EYr2EKuwhmpg-raxI_4i48DEgOZ_9njlPQGMFmj5-ppkF5gfherrR-wFX8Ps4Xqnp92YrdSG89CvbDo7FZmHr-aFovPe_N-qg672EkMcEfnF) | After \(Using Fork\)![](https://lh3.googleusercontent.com/iM14eGpAet4MnqY76xa1hcDWWYS4N6iNLc1pPXuYxExz5GOyNX4hNMLlBBMWFmRwp7LUglptYcID9wXXwphhka3LwjINwGwx6JWEJXea-teolCYpANg5pp95L3gR03PJN_UI6uCi) |
| :--- | :--- |


目的：取代掉繁雜的過程（先Clone到本機，再Push到新的Repository）

GitHub會記錄有多少人Fork，而所有的Fork都會連結到原作，除了能感謝原作的貢獻，並且能向原Repository提出更改建議。

![](https://lh6.googleusercontent.com/Dps9fvAoPr1KRGde_CA_SUp4Dl_8hh9p_Z4o11bcbb_l5DCoFKKi96IEiKZli4US4zXhB4ovKhtan8vdhLM6bf8C6JkTYcwrpcjmfkrVwgmxuppjmtON1hiJeCzK5uLnr6gUt0nB)

* 注意右上角，Fork是GitHub發明，專指在GitHub上操作的行為，並不適用於本機端

* 而Branch代表分支，但右上角的檔案並非線性發展，因此不是Branch

* Clone代表複製，無論是Remote Repository→Local或Local→Local都是Clone

## 練習：Fork Recipe Repository\(範例\)

* clone下來的repository會自動新增一個名為「Origin」的Remote Repository，不用自己手動新增

![](https://lh6.googleusercontent.com/AOASN5tAqU9l7NLSpskP0g1hfhOLeFUPgUy2xRltEGhWFnxDFunP9tz52lZKzCVIYpZv39DhdRw4JpAr2bDdFiWKUITZOILiSVxQABirpJ6VrsPSThN1iFZG9fDQWZnZ4Sbq9RTV)

* 可於Setting→Collaborators新增協作者

![](https://lh6.googleusercontent.com/K1WudaOOUgSJKxpkddO-fKWg1gfshMpKzJv9whqEb9j_4PlYNlA1BDTSEa90u9Aj21hO2-5FgvaI0_Va7hv5ExK0wA6LlW-D4YQsmS8IlWQn9EsGbTEsAXsBRIU61ReFR9zWKDYm)

註：我們所做的推送並不會影響到原作的Repository

## 協作引發的衝突\(Conflict Collaboration\)

## ![](https://lh4.googleusercontent.com/CtsHWuDSNOtpWl1dZNTjNFxuBnts3wJKJjOvjIb0PSq5aChzeydIMJDstD6uIxAJTmoFYcAHqP8aYqQnZmhPpgb6FdsBV6YNesCMUvgjWZfllL43JAW_kJdweGgOIqeJEmj__r0N)

* 時機：\(個人\)在多台裝置上編輯同個專案，\(眾人\)與他人合作時

* 此時會合併引發衝突的兩個commit

## 練習：更改Chili-recipe

| 本機端![](https://lh6.googleusercontent.com/6BrMi4XiOelsl5ShKhxDE9mQK4_IzrIOv_Zcdf7ugJoFX7IJY6MltEA_OVPaMxaU5YgFlDsxg7VROWzEw4reZLRjBPNPi2P5MdsFdelRGrN4wdPnkV9-P-ksA60clK8yxFlg4pFI) | 模擬Sarah的版本![](https://lh6.googleusercontent.com/FMlkr2LVsw8ecfMWYzcdFOjpk9F8WGd1TxvjtYmYsHPDiUaZ-nZobBAFNAtqu-weSiLEIp8W6NzUvT9yVbnkt6KmwBlrBlnXbNGFSvLqtSRqSRshscoR1jK-fNeayBDf6ydVWH4g) |
| :--- | :--- |


![](https://lh3.googleusercontent.com/aIz4nJmzEwb3dMEkayPwKB47piSoZeTRGkMHfH4YQ68kTusPFeMbPBY-rIcpMzcEVDrbtUPtedjJ3PeAp4agk85RFt1bcG2ZfUTildYUByG4Ym5u7ZOLR3q9-UjPXl2ONPkOqtPO)

## 更新Remote Branch的本地副本

## ![](https://lh6.googleusercontent.com/7U53DT4wsxzKCBsDQKjKYe1GQ9JgzZhNfdBCxwjqBN2WJz4yRF0mCYoZrfANo-X5_lCNVvpaF9MxV1ajR9mMNCSowgKYI-xWp8hQGKiTeamMvHPQePatPKVMv_yj5GYgp1YzH9G_)

上圖代表在本機端新增一個commit並指向它，會發現本機副本\(origin/master\)跟GitHub上的master並沒有更動

* 當有一個Remote Repository時，Git會將所有的Remote Branch保存一個副本到本機端，此副本會保存最後一次push/pull的Branch狀態

* 本地副本名為&lt;remote\_repository\_name&gt;/&lt;local\_branch\_name&gt;  
  如：origin/master

* 本機副本實質上也是一個branch

![](https://lh6.googleusercontent.com/qoMu1kmfEae_B37GLPa4RtINyIhb2c_JqR_LKRPxlEz9p_d8QdP7XJa4qokxTgiNeJVwfY16hrJZ-aQ_nFmBw1wdYIgUbJJeLFyGNkdlG1scc3hCZSLcDPcEDcq8USWNGBA4EXJf)

上圖代表若將local push到GitHub上，本機副本的標籤會跟著移動

![](https://lh3.googleusercontent.com/6BJ2NehVxKsZkOD9FRh_EmHQZBY6-7g3FbVP0w_N8IIuC_XP5vVwWDqjJE9NvX2SBuXeplTjE_Iy_X9sVoWMbNGC5WfADb5CUtXEEMmIEay7Na0jGYgCyovVWVNNmdRALt-zOCaN)

* 但若在本機跟GitHub上都新增一個不同commit\(a72,5b3\)，pull下來可能會發生衝突，此時可以採用git fetch在本機端新增一個本地副本\(5b3\)，避免發生衝突或覆蓋掉本機端的commit\(a72\)

* →有點類似新增一個分支，並把GitHub上新增的內容丟進去

* `git fetch` // 新增/取得一個本地副本

![](https://lh4.googleusercontent.com/l7gTSepi2Vm60qGgQZhe8qH_1w8vVgOBhcSM-40AATNZM6Wwt6P-z4K5LVQsYXENNneh1VefnKdzX3IRhXvBH7ERyE0jFNIjzT5ABvvx8zYRmW55SlURvyTxhl9Tf6pDjEBaFFC8)

* 此時可以合併抓下來的本地副本\(5b3\)跟原本本機的master\(a72\)

* 此過程可以簡化成`git pull origin master`

* git pull = git fetch + git merge // 縮寫  
  git pull origin master = git fetch origin + git merge master origin/master // 完整

* `git branch-a` // 能顯示本機+遠端的branch

![](https://lh5.googleusercontent.com/006b2EKKeofThOG81IS0NCB3P2roVI7QP_YRp6jpDqTmq2PghAg3e2bVA-h9vtCXgGXasA83-RtHTVlRT0lUXuKbL2vROQGhCgr8bz36EF54EzLCNpCDPP1GxfMJ--TqV9bp1hag)

* 特別注意這道錯了好多次的題目！

* `git status` // master 相對於 local copy 的狀態

## 合併更改

由於fetch下來的origin/master跟本機的master內容有不同，因此輸入`git status`後會提示diverged

```bash
$ git status
On branch master
Your branch and 'origin/master' have diverged(分歧), and have 1 and 1 different commit each, respectively.
(use "git pull" to merge the remote branch into yours)
nothing to commit, working directory clean
```

* `git checkout master` // 先切換到master branch

* `git merge master origin/master` // 合併他們  
  注意：此時會出現合併衝突，因此需要更改檔案來解決

```bash
$ git merge master origin/master
Auto-merging chili-recipe.txt
CONFLICT (content): Merge conflict in chili-recipe.txt
Automatic merge failed; fix conflicts and then commit the result.
```

注意：更改好衝突檔案\(chili-recipe.txt\)後，記得要先add和commit，不可以直接merge，否則會出現以下錯誤：

```bash
$ git merge master origin/master
error: merge is not possible because you have unmerged files.
hint: Fix them up in the work tree, and then use 'git add/rm <file>'
hint: as appropriate to mark resolution and make a commit.
fatal: Exiting because of an unresolved conflict.
```

注意：合併時不能只commit部分\(`git commit chili-recipe.txt`\)，需要commit整體\(`git commit`\)

```bash
$ git commit chili-recipe.txt
fatal: cannot do a partial commit during a merge.
```

步驟整理：

1. `git fetch`

2. `git checkout master`

3. `git merge master origin/master`

4. 更改好合併衝突

5. `git merge master origin/master` \(須先add\)  
   `git add chili-recipe.txt`

6. `git commit chili-recipe.txt` \(不能只commit部分，要commit整體\)  
   `git commit`

7. `git merge master origin/master`

上面步驟可以簡化成`git pull origin master`

```bash
$ git status
On branch master
Your branch is ahead of 'origin/master' by 2 commits.
  (use "git push" to publish your local commits)
nothing to commit, working directory clean
```

若出現上面的錯誤，代表目前master超前local copy兩個commit，因此需要更新\(push上去\)使本機跟GitHub上相符

`git push origin master`

## 其他

* Git Bash中沒有`cd..`的指令\(Windows版\)，需使用`cd ../`\(Mac版\)才可以，但`ls`跟`dir`都能夠顯示檔案清單  



