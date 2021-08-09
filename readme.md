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

# 使用しているツール（VSCode拡張）
- VSCode Remote Container

# 使用しているツール（node.js関連）
- typescript
- ts-node-dev

# 実行方法
1. npm run dev を実行  
  (何を実行しているかはpackage.jsonファイルの「dev」の定義を参照)

# 補足
- Typescriptファイルはコンパイルしてからデプロイする。  
  そのためTypeScriptのモジュール自体はdevDependenciesに格納
- 本来であればRemote Containerを使用してコンテナ内で開発環境を完成させたかったが、Windowsだとファイルシステムの関係上ホットリロードが出来ないため
  WindowsはNode.jsをインストールする必要がある。LinuxOrMacであればおそらくできるはず