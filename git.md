- 以[notes](https://github.com/wu-shang-ru/notes)這個倉庫為範例

---

# 創建clone連結

1. 首先我們到想要fork的地方，點選fork按鈕。

2. 接下來到自己本身的github上面複製clone網址。

3. 在桌面創建一個資料夾，進入資料夾並開啟cmd，輸入 git clone `https://github.com/(因人而異)/notes.git`。

4. 確認是否有資料被pull下來。

# pull push 以及 發PR的流程

1. 先輸入`git remote add upstream https://github.com/wu-shang-ru/notes.git`建立上游。

2. 輸入`git remote -v` 確認有無上游。

3. 輸入`git pull upstream master`將上游資料更新至本地端，若無更新資料則無反應。

4. 若有資料更新需上傳，輸入`git status`檢查檔案狀態，若有更新資料但尚未被.git標記，則會顯示為紅色。

5. 輸入`git add .`即可標記資料，此時輸入`git status`會顯示為綠色。

6. 將資料commit註解，輸入`git commit -m '(任意)'`即可將更新的資料加上commit。

7. 輸入`git push -u origin master`，將檔案推送至github上。

8. 至自己的github上按下`New pull request`按鈕，並送出，即可完成一次PR發送。

- 每次欲更新檔案時，記得先pull上游看看有無更新資料，以免檔案衝突。

---

# 分支

- git branch 確認擁有的分支
- git branch xxx 新增分支

- git checkout dev 切換分支

- git merge rogerBranch 合併分支 (在要合併的分支上輸入)

- git log --oneline 確認git commit 資料

- git branch -d <> 刪除分支

- git reset --hard HEAD~ 回復至上一個commit紀錄
