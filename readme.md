# このプロジェクトについて
node.js を使ってAPIを作ろうのプロジェクト

# 使用している技術
- node.js
- docker
- docker-compose
- mysql

# 使用しているツール
- vscode
- git
- docker desktop for windows

# 使用しているVSCode拡張
- VSCode Remote Container

# 使用しているnode.jsのパッケージ
- typescript  
  JavaScriptに型を導入する
- ts-node-dev  
  ホットリロード有効にするため(開発効率向上)
- Express
  APIを実装するためのフレームワーク
- eslint
  コーディングルールの統一のため(開発効率向上)
- prettier
  コーディングルールの統一のため(開発効率向上)
- TypeORM
  TypeScriptのORM  
  ~~Entityを定義するときは型アサーション「！」を入れるか、ファイルの先頭に「// @ts-nocheck」を入れる必要がある点に注意~~
  ~~これはtsconfigの「"strictPropertyInitialization": false」のせいでプロパティをコンストラクタで初期化しない場合にはエラー出すようになっているため~~  
  以下のガイドラインに沿ってEntityを定義することに決定  
  https://tech.bitbank.cc/typeorm-entity-guideline/

# 実行方法
1. VSCode Remote Containerを使用してコンテナへログインする  
   (画面左下のReopen In Containerを選択することでログインができる)
2. TypeORMのマイグレーションを実行する  
   (この操作はプロジェクトを落としてから１回実行するだけでOKです)
   「npx ts-node-dev ./node_modules/typeorm/cli.js migration:run」
3. npm run dev を実行
   (何を実行しているかはpackage.jsonファイルの「dev」の定義を参照)

# 本番環境へのデプロイ方法
以下プロセスは全てDockerを使用して行う想定  
参考URL：https://dev.eringiv3.com/blog/post/run_typescript_app_on_docker_container  
参考URL：https://github.com/catman85/TermApp-Node-Typesript-Docker-Express
1. TypeORMで出力したマイグレーションファイルを実行
   (これ自体はどうするか。。。Dockerでマイグレーション用のイメージを作る？)
2. TypescriptをJavascriptへ変換  
   (このプロセス自体はDockerを使用して実行する予定)
   (変換したJavaScriptはDistフォルダへ出力される)
3. 出力したファイルをNodeで実行する

# マイグレーションについて
以下のコマンドを打てばEntityフォルダをもとにしてマイグレーションファイルを出力してくれる
「npx ts-node-dev ./node_modules/typeorm/cli.js migration:generate -n Test」
出力した後は以下のコマンドを打つことで実際にDBにマイグレーションが行われる
「npx ts-node-dev ./node_modules/typeorm/cli.js migration:run」
マイグレーションしたファイルをロールバックしたい場合は以下のコマンドを実施すること
「npx ts-node-dev ./node_modules/typeorm/cli.js migration:revert」
本番環境にマイグレーションを行う際にはきっちりとテストしたファイルをマイグレーションすること
間違ってもロールバックすることはないはず。。。

# 補足
- Typescriptファイルはコンパイルしてからデプロイする想定。  
  そのためTypeScriptのモジュール自体はdevDependenciesに格納
- eslintとprettierを導入しているため、「npm run lint」を実行することで、コーディングルールに則っていない  
  コードは自動的に整形される。　　
  コーディングルールは導入時に必要最低限としている。ルールを追加したかどうかは設定ファイルである
  「.eslintrc.js」と「.prettiertc.js」のコミットログを追跡すること