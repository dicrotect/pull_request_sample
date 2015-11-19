# pull request の練習リポジトリ

GithubのREADMEファイルはGithubマークダウン記法を使って記述する。
[markdownで行こう](https://gist.github.com/wate/7072365)

## git -> Githubへのpush(流れ)
1. ローカル上でディレクトリ作成(プロジェクト)
2. ディレクトリ内で`git init` コマンドを使い初期化
3. 何かしらの作成 or 編集
4. `git add ファイル名`コマンドで更新したものをステージングエリアに上げる
5. `git commit -m "コメント"`コマンドで変更を保存する
6. Github上でリモートリポジトリを作成
7. git remote add と git pushのコマンドをコピー
8. `git remote add origin githubのURL`コマンドでローカルとリモートを接続
9. `git push -u origin master`コマンドで保存したソースコードをリモートへ送る

##pullの流れ
1.リモートリポジトリをローカルにあげる
2.`git pull origin master`コマンドでリモート上の最新リポジトリをローカルに持ってくる

## Pull Requestの流れ
1.`git checkout -b ブランチ名 `コマンドで新規ブランチを確作成（同時にブラウザの切り替えを行ってくれる）
2.何かしらのupdateをする
3.`git add `.`git commit -m`の順で保存する
4.`git push origin 新しいブランチ名`コマンド上に新しいブランチを作成してpush
5. Github上でpullrequestをマージ
6. 管理者がrequestをレビューする
7. 問題があれば差戻す
8. 再度問題を修正し`add` `commit` `push`で修正内容を pull reqに上書きして送る
    + pull req中に同じブランチに修正内容をpullするとそれだけで修正内容がpull reqにのっかる
9. 修正内容を確認しmargeする
10. ブランチを削除する

###ブランチの切り替え方
+ `git checkout ブランチ名` コマンドでブランチを行き来できる
    + 現在いるブランチで変更を行っていた場合はその変更内容を保存もしくは削除してからブランチを移動すること

###commitコメントの修正
`git commit --amend -m "新規コメント"`で編集可能(mを間違えた時)

###指定したcommitでコードを遡る方法
1. Github上で（もしくはlog上）でcommitのハッシュをコピー
2. `git checkout ハッシュ`コマンドで指定したcommitへもどる
3. `git checkout ブランチ名`コマンドで最新のコマンドにもどる

###別ブランチのcommitをマスターブランチに追加
1. 別ブランチでのcommitを変更しきる
2. git log --onelineでcommitのハッシュを見る
3. `git checked master`でmasterブランチに移動
4. `git cherry-pickハッシュ`で別ブランチのcommitをmasterへ追加

###ローカルブランチの削除
+ `git branch -d ブランチ名`
+ もしerrorがでたら`git branch -D ブランチ名`で強制削除も化
