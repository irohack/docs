# docsにページを追加する。
## あらかじめ
あらかじめやっておくことー！
1. pythonのインストール
2. githubリポジトリの権限をもらう

### pythonのインストール
pythonの最新版くらいはインストールして、以下のコマンドを実行できるようになっておいてください。

```
$ python --version
$ pip --version
```

### githubリポジトリの権限をもらう
yakinikuに言ってリポジトリ編集の権限をもらっておいてください。当然ssh公開鍵登録も忘れずにしておいてください。

## やります
### mkdocsのインストール
pipを用いてmkdocsとデザインテーマであるmaterialをインストールします。

```
$ pip install mkdocs
$ pip install mkdocs-material
```

### cloneする
自分のワークディレクトリでgit cloneします。 cloneしたらcdでdocsプロジェクトディレクトリ内に入っておきましょう。

```
$ git clone git@github.com:irohack/docs.git
```

### ローカルで確認する
編集してもgithubにpushしないと確認できないとかマジめんどくさいの極みなので、ローカルで確認します。mkdocsが勝手にビルドしてローカルサーバー立ち上げてくれるので使わせてもらいましょう。プロジェクト内で↓

```
$ mkdocs serve
```

そしたら、``Serving on http://127.0.0.1:8000``みたいなのが出ると思うんで、アクセスしましょう。welcomeできているはずです。

## 編集する。
### ファイル構成
ファイル構成はこんなかんじになっています。

```
docs / docs
       site
       node-modules
       mkdocs.yml
       package-lock.json
```

基本的に編集するのはdocsディレクトリ内です。

### なんか追加する。
docsに各ページをmarkdown形式で追加・編集できます。（～.md）
とりあえず、なんか追加しましょう。プロジェクト内で↓

```
$ echo "#hello" -> docs/example001.md
``` 

そしたら、勝手にサイトがリロードされて更新されたと思います。んで、example001.mdが追加されてるはずです。これで編集方法はおしまい。markdown記法などはググってください。

## 更新をアップロードする
### デプロイする。
デプロイの意味は調べてください。本来はサーバにあげるなど面倒な手順を踏まないといけないですが、mkdocsはこれもやってくれます。便利ですね。

```
$ mkdocs gh-deploy
```

これで[このサイト](https://irohack.github.io/docs/)は更新されたはずです。（ちょっと時間がかかることがある）仕組みはgithubのgh-pagesブランチにpushしてくれています。mdをhtmlにしたりもせず、このコマンドだけでやってくれるのでめちゃ便利ですね。

### pushする
デプロイだけしちゃうと後後他の人が更新するときに編集ファイルが古いもので困ってしまいます。きちんとgithubのmasterブランチにpushしましょう。

```
$ git add .
$ git commit -m "コメントはちゃんとつけてね"
$ git push -u origin master
```

おしまいです