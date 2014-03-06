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

> ProGitを読むといい．日本語もある．
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

> git push サーバーの名前　手元のブランチの名前

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

そうすると中岡さんにいつも見ている変なメールが来る．



```bash
git remote
```
originって出る．

```bash
git remote show origin
```

中岡さんの変更を取り込みたい．

```bash
git remote add tnaka-nandemoii git@github.com:tnaka/git-test.git
```

> git remote add 何でもいい url
>> .git/configが変わるだけ


```bash
git remote
```
とすると増えている．

```bash
git branch -a
```
で色々見えるけど，中岡さんのoriginしか見えていない


```bash
git fech tnaka
```
でtnakaのサーバー上の変更をとれる．

```bash
git branch -a
```

で見るとnakaokaさんのmasterも見えるようになった．



```bash
git checkout master
git branch -vv
```

ここでいうmasterは上田さんのマスター

> gitkでそれっぽいのが見える．

中岡さんも色々変更しているのでそれが欲しい．
中岡さんのマスターが欲しい．

```bash
git merge tnaka/master
```

これで中岡さんのmasterが手に入る．

```bash
git checkut -b more-awesome-code
echo "aaa" > awesomecode.sh
git status
```
awesomecode.shを編集したので，中岡さんに取り込んでもらいたい．
```bash
git add awesomecode.sh
git commit -m "more awesome"
```

> gitk見ると一個前に進んだ．

```bash
git push tnaka more-awesome-code
```

としてみると中岡さんのレポジトリにpushしようとするが，権限がないので無理．

```bash
git remote -v
```

```bash
git push origin more-awesome-code
```

> git は結構tab補完がきく

webからPRを送る．

PRのメッセージは画像とかも貼れる．

断られたらさらに変更して，自分のブランチにpushすれば良い．

```bash
echo "bbbbbb" > awesomecode.sh
git status
git add awesomecode.sh
git commit -m "very awesome"
git push origin more-awesome-code
```

これでgithubみると同じスレッドで話が進んでいる．
pushしただけでは中岡さんには通知は行かない．
コメント書けば通知が行く．

```bash
git checkout master
git fetch --all
git merge tnaka/master
git branch -a
```

[ここ](http://git-scm.com/book/en/Git-Branching-What-a-Branch-Is)がコミットの概念を説明している．

コミットグラフは
* gitk
* tig
* git log --oneline --decorate --graph --branches --tags --remotes
* emacs の magit

などなどで見やすく見れる．
