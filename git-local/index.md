# git 本機端操作

## 目錄
- [回目錄](../SUMMARY.md)

## 常用 linux 指令清單

```
// 清除螢幕
{ctrl} + {l}

// 查看當下資料夾內容
ls 

// 顯示某個檔案內容
cat {fileName}

// 建立資料夾
mkdir {folderName}

// 建立文字檔案
touch {fileName}

// 編輯文字檔案
vim {fileName}

// 刪除檔案
rm {fileName}
```

***

## 常用 git 指令清單
```
// 設定使用 git commit/git log 時顯示的使用者名稱
git config --global user.name "你的名字"

// 設定使用 git commit/git log 時顯示的信箱
git config --global user.email "你的信箱"

// 建立本機 git repository
git init

// 新增檔案到 git 
git add {fileName}

// 新增全部檔案到 git
git add .

// 提交變更
git commit 

// 快速提交變更
git commit -m "訊息"

// 快速提交變更且選取全部檔案
git commit -m "訊息" --all

// 修改上一次的 commit 訊息
git commit --amend

// 顯示當下 git repository 狀態
git status

// 顯示變更歷史訊息
git log

// 顯示變更歷史訊息以及變更內容
git log -p 
git log -p --word-diff

// 顯示最後一個 commit 的歷史訊息與變更內容
git show

// 比對上次 commit 跟現在的工作目錄差異
git diff

// 比對某個 commit 跟現在的工作目錄差異
git diff {commit}

// 比對某兩次的變更內容
git diff {commit1} {commit2}

// 取消最近一次的變更
git checkout .

// 切換至某個分支
git checkout {remoteName} {branchName}

// 建立新分支
git checkout -b {branchName}

// 查看當下 branch
git branch 

// 還原工作目錄至上一次 commit 之狀態
git reset 

// 還原工作目錄至某次 commit 之狀態，但是保留目前變更
git reset {commit}

// 還原工作目錄至某次 commit 之狀態，放棄目前變更
git reset {commit} --hard

// 暫存目前工作目錄狀態
git stash

// 檢視目前已經暫存的工作目錄狀態佇列
git stash list

// 套用某次的暫存變更
git stash apply {stash{x}}

// 取出上一次暫存的工作目錄狀態
git stash pop

// 清除已經暫存的工作目錄狀態佇列
git stash clear

// 合併兩個分支
git merge {branch1} {branch2}
```

***

## 常用 vim 指令
```
// 進入編輯模式
{i} key

// 離開編輯模式
{esc} key

// 離開編輯器
:q

// 儲存變更並離開編輯器
:wq
```

***


## git local 端操作流程

課程內容使用 HelloJS 專用 VM 進行操作，以下按照順序列出課程依序會使用到的指令。

![](../img/hellojs-vm.png)

```
// 建立資料夾與 init git repository

mkdir git-local

ls

cd git-local

git config --global user.name "kent"

git config --global user.email "kent@trunk-studio.com"

git init


// 建立檔案與 commit 工作目錄變更 

touch myfile

vim myfile

git status

git add myfile

git commit -m 'this is my first commit for myfile'

git log

git show

vim myfile

git add .

git commit -m 'my second commit'

git log


// 查看歷史變更紀錄與比對紀錄

git diff {comment1} {comment2}

git show

git log -p

git log -p --word-diff

git show --word-diff

// 修改 commit 訊息

git commit --amend

git log


// 還原變更

vim myfile

git status

git checkout myfile

git status


// 還原工作目錄至某狀態，但保留變更

vim myfile

git commit -m 'my third commit' --all

git log

git reset {1st commit}

git log

git status

cat myfile

// 還原工作目錄至某狀態，放棄變更

vim myfile

git commit -m 'my new second commit' --all

git log

git reset {1st commit} --hard

git log

git status

cat myfile


// 建立新分支

vim myfile

git commit -m 'my super new second commit' --all

git log

git branch

git checkout -b develop

git log

git branch


// 切換分支

vim myfile

git commit -m 'my first commit for develop branch' --all

git log

git checkout master

git log

git branch


// 使用 checkout 放棄變更

vim myfile

git status

git checkout myfile

git status


// 使用 stash 在不同 branch 間切換工作目錄狀態

vim myfile

git status

git stash

git status

git stash list

git stash show stash@{0}

git checkout develop

git stash pop


// 解決衝突

git status

vim myfile

git status

git commit -m 'fix conflict' --all

git log

cat myfile


// 合併分支

git checkout master

git branch

git merge master develop

git log

cat myfile
```

***

## 下一頁
- [回目錄](../SUMMARY.md)
- [git 多人協作](../git-remote/index.md)