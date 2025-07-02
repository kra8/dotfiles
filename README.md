# Dotfiles管理

このリポジトリは設定ファイル（dotfiles）をGitで管理するためのものです。

## 設定

[`dotfiles.yml`](dotfiles.yml:1)で管理対象のファイルやディレクトリを定義します：

```yaml
files:
  - .claude/
  - .zshrc
```

## 使用方法

```bash
# 実際のホームディレクトリから設定ファイルを取得
task pull

# 設定ファイルをホームディレクトリにコピー
task push

# 設定ファイルをホームディレクトリにシンボリックリンク
task link

# 管理対象ファイルの状態を確認
task status
```

## ディレクトリ構造

```
dotfiles/
├── Taskfile.yml
├── dotfiles.yml
├── README.md
└── HOME/            # 設定ファイルの保存場所
    ├── .claude/
    └── .zshrc
```

## 使用例

### 初回セットアップ

1. [`dotfiles.yml`](dotfiles.yml:1)に管理したいファイルを追加
2. 設定ファイルを取得
```bash
task pull
```
3. Gitでコミット
```bash
git add .
git commit -m "Add dotfiles"
```

### 他の環境での適用

```bash
git clone <このリポジトリ>
cd dotfiles
task link
```

## 仕組み

- `task pull`: `$HOME` → `./HOME/` にファイルをコピー
- `task push`: `./HOME/` → `$HOME` にファイルをコピー  
- `task link`: `./HOME/` → `$HOME` にシンボリックリンクを作成
