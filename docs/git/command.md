# Learn Git

- [Learn Git](#learn-git)
  - [`git status`](#git-status)
  - [`git add`](#git-add)
  - [`git checkout`](#git-checkout)
    - [`git checkout -b`](#git-checkout--b)
  - [`git branch`](#git-branch)
  - [`git reset`](#git-reset)
  - [`git revert`](#git-revert)
    - [Cách 1:](#cách-1)
    - [Cách 2:](#cách-2)
  - [`git merge`](#git-merge)
  - [`git diff` - Hiển thị các thay đổi giữa các lần commits, commit and working tree.](#git-diff---hiển-thị-các-thay-đổi-giữa-các-lần-commits-commit-and-working-tree)
  - [`git remote`](#git-remote)
    - [`git remote add [<options>] <name> <url>`](#git-remote-add-options-name-url)
  - [`git remote show [<options>] <name>`](#git-remote-show-options-name)
  - [`git push <remote-name> <branch-name>`](#git-push-remote-name-branch-name)
  - [`git fetch`](#git-fetch)
  - [Git-flow](#git-flow)
  - [Extensions](#extensions)

### `git status`

### `git add`

Ví dụ add 1 file:

```cmd
git add <file-path>
```

Ví dụ add nhiều files:

```cmd
git add <file-path-1> <file-path-2> <file-path-3>
```

### `git checkout`

Ví dụ: switch giữa các nhánh

```cmd
git checkout dev // switch sang nhánh dev
git checkout main // switch sang nhánh main
```

Ví dụ:

#### `git checkout -b`

### `git branch`

```cmd
git branch [<options>]
```

_Options:_

- `-a, --all` List both remote-tracking and local branches
- `-d, --delete` Delete fully merged branch
- `-D` Delete branch (even if not merged)
- `-m, --move` Move/rename a branch and its reflog
- `-l, --list` List branch names

### `git reset`

```cmd
//
```

### `git revert`

#### Cách 1:

Giả sử như có các commits:

```cmd
commit 363615767b1d0c8febef3dfcec68fa40e073274e (HEAD -> main)
     5

commit ffebf6b75ca2b8453ff2a50f8d941d431024308d

commit a8003514fd704763ce6dad51fc1a6ad84a75b435

    2

commit d1b8ccb74b207e081ea0d810722ceb95c91c51aa

    1

commit 3621990b9715f192ae14d6953e7aae8bbf96e081

    Root

```

Revert về commit a75b435 (2). Còn code của commit 1, xóa all

```cmd
git revert no-commit a8003514fd704763ce6dad51fc1a6ad84a75b435
```

#### Cách 2:

```cmd
git checkout <commit-id>  // checkout về commit cần quay lại

git checkout -b <tên nhánh mới> // làm gì đó với nhánh này
git commit // nếu cần

// Với nhánh cũ thì có thể xóa đi hoặc đổi tên nếu muốn
git branch -D <tên branch cũ> // xóa đi
git branch -m <tên branch cũ> <tên branch mới>

```

### `git merge`

### `git diff` - Hiển thị các thay đổi giữa các lần commits, commit and working tree

- Cách 2 là gõ git status

### `git remote`

#### `git remote add [<options>] <name> <url>`

### `git remote show [<options>] <name>`

### `git push <remote-name> <branch-name>`

```txt
--all
--tags
```

### `git fetch`

### To delete branch `git branch -D <local branch name>`

### To delete remote branch `git push <host name, eg: origin> --delete <remote-branch-name>`

## Git-flow

[Original article](https://nvie.com/posts/a-successful-git-branching-model/)

![git models](git-asset/git-models.png)

## Extensions

- Git graph
- Git len
