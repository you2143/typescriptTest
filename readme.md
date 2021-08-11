# このプロジェクトについて
node.js を使ってAPIを作ろうのプロジェクト

# 使用している技術
- node.js
- docker
- docker-compose
# 使用しているツール
- vscode
- git
- docker desktop for windows

# 使用しているVSCode拡張
- VSCode Remote Container

# 使用しているnode.jsのパッケージ
- typescript
- ts-node-dev
- Express

# 実行方法
1. npm run dev を実行
  (何を実行しているかはpackage.jsonファイルの「dev」の定義を参照)

# 本番環境へのデプロイ方法
以下プロセスは全てDockerを使用して行う想定  
参考URL：https://dev.eringiv3.com/blog/post/run_typescript_app_on_docker_container  
参考URL：https://github.com/catman85/TermApp-Node-Typesript-Docker-Express
1. TypescriptをJavascriptへ変換  
   (このプロセス自体はDockerを使用して実行する予定)
   (変換したJavaScriptはDistフォルダへ出力される)
2. 出力したファイルをNodeで実行する
# 補足
- Typescriptファイルはコンパイルしてからデプロイする。  
  そのためTypeScriptのモジュール自体はdevDependenciesに格納
- 本来であればRemote Containerを使用してコンテナ内で開発環境を完成させたかったが、Windowsだとファイルシステムの関係上ホットリロードが出来ないため
  WindowsはNode.jsをインストールしてWindows上で実行する必要がある。LinuxOrMacであればおそらくできるはず