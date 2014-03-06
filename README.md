git-practive
============
## 一度pushしてしまったbranchを消したい
```bash
touch fuga
git add fuga
git commit -m "hoge"
git push -u origin master
```

してpushした後に

```bash
git branch fuga
git branch -vv
```

するとfugaだけremoteとの対応がとれていない．
trackingという．

```bash
git push -u origin mfuga
```

してから

```bash
git branch -vv
```

すると対応がとれていることがわかる．

```bash
git branch -d fuga
git branch
```

消えてるように見えるが引っ掛けで，

```bash
git branch -a
```

とするとremoteのブランチも出てきて，fugaがある．

これを消すには

```bash
git push origin :fuga
git branch -a
```

消える!

## アカウントを作る
アイコンを顔にして下さい  
by 垣内さん

## Travis
jenkinsとおんなじようなやつ
privateリポジトリだと高いが，publicだと無料．
pushしたらテストしてくれる．

## みんなでPRを送る練習


## branchを作る
```bash
git branch add-hello-world
```

```bash
git branch
```

だとリストになる

```bash
git checkout add-hello-world
git branch
```

移動していることがわかる

HelloWorldをガシガシ作る

で，おもむろに

```bash
git status
```

と打ってみる．

## Untracked files
gitが管理していないファイルのこと．
ここでは
* Makefile
* hello_world
* hello_world.cpp
がある．

>>> ProGitを読むといい．日本語もある．
[ここ](http://git-scm.com/about/staging-area)の話

git は3つ領域がある．

作業しているところはディレクトリ

.gitにいろんなファイルが隠れている．

普段見えているのがworking repository

git が持っているのが repository

```bash
git add hello_world.cpp
git add Makefile
```

とかとか．

```bash
git log --graph --branches
```

```bash
git branch
```

```bash
git chekcout master
git branch
ls
```

- hello_world.cppとMakefileが消えていることがわかる

```bash
git merge add-hello-world
```

で持ってこれる．

```bash
ls
```
- hello_world.cppとMakefileが帰ってきた

```bash
tig
```

でいい感じで見える．



```bash
git push
```

webでみると追加されているのが確認できる．

コミットのネットワークを作っていく．
コミットグラフという．



## fork
中岡さんのレポジトリを上田さんがcloneした上で，

```bash
git branch add-awesome-code
git checkout add-awesome-code
touch hogehoge
git add hogehoge
git commit -m "add awesome"
git push origin add-awesome-code
```

権限がないので弾かれるが，素晴らしいコードなのでぜひとも取り込んでほしい．

githubのページでforkボタンを押す．

自分のgithubにレポジトリができる．

ので，上田さんが上田さんのrepositoryを取ってくる．

```bash
git clone hogehoge git-test-garaemon
cd git-test-garaemon
touch fugafuga
git add fugafuga
git commit -m "add awesome"
```

>>> git push サーバーの名前　手元のブランチの名前

origin : cloneしたときのurl

```bash
git remote show origin
```

でoriginの情報が見れる．

今からpushします

```bash
git push origin add-awesome-code
```

>>>これ以上のpushの書き方はググって下さい．

今回は弾かれない．成功している．

これを是非中岡さんのレポジトリに持って行きたい．

githubのページからプルリクを送れる．
