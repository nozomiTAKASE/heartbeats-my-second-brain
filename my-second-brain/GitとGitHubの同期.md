# Git と GitHub の同期（この保管庫）

この保管庫はローカルの Git で管理し、リモートは GitHub（SSH）です。

- **リポジトリのルート**（ターミナルで `cd` する場所）:  
  `Documents/my-second-brain`  
  （中に `my-second-brain` フォルダ＝Obsidian の保管庫本体があります）

---

## いつもの更新（自分の Mac で編集したあと）

ターミナルを開いて:

```bash
cd /Users/p0063/Documents/my-second-brain
git status
```

変更をまとめてコミットしてプッシュ:

```bash
git add -A
git commit -m "メモの更新"
git push
```

- **`-m` のメッセージ**は内容が分かるように変えてよいです（例: `日記追加`, `リンク整理`）。
- 変更がないときは `commit` は「nothing to commit」と出てスキップされます。

`main` の初回だけ upstream を付けた場合は、2 回目以降は `git push` だけで十分です。

---

## 他の場所で編集したあと（GitHub や別 PC で変えた場合）

先に取り込んでから続きの作業すると安全です。

```bash
cd /Users/p0063/Documents/my-second-brain
git pull
```

コンフリクトが出たら、該当ファイルを開いて `<<<<<<<` などを手で直し、`git add` → `git commit` → `git push` します。

---

## うまくいかないとき

| 症状 | 確認すること |
|------|----------------|
| `Permission denied (publickey)` | GitHub の [SSH keys](https://github.com/settings/keys) に、この Mac の**公開鍵**が登録されているか |
| 認証は通るが push できない | そのリポジトリへの**書き込み権限**があるアカウントで SSH しているか（`ssh -T git@github.com` で表示されるユーザー名） |

---

## 関連

- リモート URL の確認: `git remote -v`
- `.gitignore` で Obsidian のウィンドウ状態など一部ファイルは追跡しない設定になっています。
