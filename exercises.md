## 第3題

![](https://lh4.googleusercontent.com/2AbuXeImGwdXt0GinmCVUwspSLMxwDJk06WVN6kyP3DDc5DTADmhgyEaEKGIPMLZkDFh2fNHuU8V9ArLHPX_v7SADL_XF90QpHSL7DgyJ9kTdKjxdI_g6eNKlSvwM7hY4xh5Rc9f)

* 剛開始錯第一小題\(註:上圖為正解\)，原本以為「直接」存取舊版本代表可以直接開啟，想說要經過兩步驟  
  \(1.git log 查找 commit id, 2.git checkout 到指定版本\)

> 官方詳解：  
> This is false. You could still access the old version of the file by checking out the commit associated with that version. Then the recipe would temporarily revert to its state at the time that commit was made.

## 第5題

![](https://lh5.googleusercontent.com/-zBFI14xRK9QzdX88TRO3Ns_RUpjMbBhoPuoHAGYruWIKTrKq8XtAAmkMxg7gHhcAXZr9rZnsevXHu6_mpV4AMwwiJeoFv744L73dm7oltIIu-ojo2pcPdefyiHKYtFGLaAMrw2O)

* 注意第四小題，原本以為「State」代表是commit中的ID,author跟message，但這邊強調的是「原封不動地保留\(複製\)全部檔案」的狀態

> 官方詳解：This is true for both copying a directory and cloning a repository. In both cases, all the files are copied.

* clone相較於copy的優點是能夠保留完整的歷史變更\(git log\)

* repository可用 git clone 複製，而directory也可用 scp 複製  
  原文：For copying a directory, you weren't expected to know this, but it is possible to copy a directory from one computer to another using the command scp, which stands for "secure copy". The name was chosen because the scp command lets you securely copy a directory from one computer to another.

## 第6題

![](https://lh6.googleusercontent.com/MzKhIYwzQ9BTI3eu3rXVNSLcPVdnjQSx0_8Mq9ZmnnfTEzMEZPVsdV4TmtJqwrqiJ58BjTRwQTJG8mKP_OQfxDljM4e3RyqHSntO7PNilJbbTJStfYtgXGB4ALTJ-Ohulap4gvTt)

* 當初沒注意到是複選題，只有選第二個選項

* 不只有新增功能的那版本要選，還要選之後全部的版本\(除非後來有移除功能\)

## 第8題

![](https://lh4.googleusercontent.com/bY8CDVJ4x7bn6hHaBOzuXtWl8_IztP9vkmv-q0W8Rk0_GCRAw-Qr2xI9hOf5rXQN7JeRsSrrQJizrXdO9jDbvBsF0vMYzHedxNxiFisUJTMzbZpQv2Adz-Zz3GrpGnP5ocmzxs2q)

* 注意第一小題，一開始選擇Always true

* 若有版本1,2,3，而1和3的內容相同，則從3還原到1時不會影響到任何檔案

> 官方詳解：
>
> This is sometimes true.Git doesn't allow you to save a new commit if no files have been updated, so you might think this is always true. However, it's possible to do the following:
>
> * Save a commit \(call this commit 1\).
>
> * Update some files and save another commit \(call this commit 2\).
>
> * Change all the files back to their state during commit 1, then save again \(call this commit 3\).
>
> This sometimes happens if commit 2 contained a bug, and it's important to fix the bug quickly. The easiest thing to do might be to remove all the changes introduced by commit 2 to fix the bug, then figure out how to safely reintroduce the changes later.
>
> At this point, commit 3 is the latest commit, so if you checkout commit 1, none of the files will be changed.

* 注意第四小題，原本誤解題目是說checkout後檔案狀態保持不變，因此選擇Never true。但後來瞭解到他強調的是Checkout保存當下的Snapshot\(快照\)，因此可以即時地還原到指定的狀態

> 官方詳解：This is always true. A commit saves a snapshot of all files in the repository at the time the commit was made, so checking out an earlier commit will result in all the files being reverted to their state at the time the commit was made. That is, the files will be in a consistent state.

## 第13題

![](https://lh6.googleusercontent.com/jQVjG3k9TWlUR5aoJ7gOqLQX4JayO8Kqx0lePYqMtWTdaiC2beAuFfCDkzzDai3UDHCZzUdYfIspv8e0FjO1PB5aD8mg33WhoNEWLERoW16lXN2qBk7h7IuacY9mK03aHb4V5_Li)

![](https://lh6.googleusercontent.com/a4OzgzAAhcZ-ej2Cvk2pJd4s_psii-NQDJdXcQa_G319i7VGGZMtpcFZFbLc3XVFzWzVyK1FGdgwwY4nIWNpUN2v0PM3-kHSQuT6ocu3WEykXBYrVFJ0e7WTD-tUvbXw0GeuA8wa)

* 注意第一小題，原本選第一個選項，但後來發現\(x,y\)代表選擇x~y之間的數，並非固定不變的數

> 官方詳解：That is, the x and y coordinate of each clone is changed by a larger random amount. This will have the effect of making the clones move more quickly, or speed up, since their positions change more quickly.



