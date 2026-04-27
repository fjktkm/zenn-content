---
title: "Dev Container のハンズオン"
---

## Dev Container とは

Dev Container は，Docker コンテナを開発環境として使うための仕組みです．Dev Container を利用するメリットには次のようなものがあります．

- 環境構築の手間を削減できる
- プロジェクトごとに独立した開発環境を利用できる
- チームで同じ開発環境を共有できる

## プロジェクトフォルダを作る

はじめに，開発環境を構築するプロジェクトフォルダを作ります．エクスプローラーを開きフォルダを作成してください．フォルダの場所はどこでも構いません．フォルダの名前は `latex-devcontainer-book` とします．

ソフトウェア開発においては，プロジェクトごとにフォルダを作り，そのフォルダを起点として作業を進めることが一般的な慣習となっています．あらゆる開発用のツールはこのことを前提に作られています．このような慣習を受け入れることで，ツールの恩恵を最大限に受けることができます．

## VS Code でプロジェクトフォルダを開く

VS Code を起動し，先ほど作成したプロジェクトフォルダを開きます．推奨する手順は次の通りです．

1. VS Code のウィンドウの上部のメニューから「ファイル > フォルダを開く」を選択する
2. フォルダ選択のダイアログが表示されたら，先ほど作成したプロジェクトフォルダを選択する
3. 「フォルダの選択」ボタンをクリックする

また，次のような手順でも同様にプロジェクトフォルダを開くことができます．

1. 先ほど作成したプロジェクトフォルダをエクスプローラーで開く
2. エクスプローラーの上部のアドレスバーを選択する
3. アドレスバーに「code .」と入力して Enter キーを押す

## Dev Container の構成ファイルの作成

VS Code でプロジェクトフォルダを開いたら，次に Dev Container の構成ファイルを作成します．推奨する手順は次の通りです．

1. VS Code のウィンドウの左下にある「><」のアイコンをクリックする
2. 表示されたメニューの中から「開発コンテナ構成ファイルを追加する…」を選択する
3. 「コンテナー構成テンプレートを選択するか，カスタムテンプレート ID を入力します」という質問項目について「ubuntu」と入力し「Ubuntu」を選択する
4. 「Ubuntu version:」という質問項目について，なにも選択せず Enter キーを押す
5. 「インストールする追加機能を選択する」という質問項目について，なにも選択せず Enter キーを押す
6. 「次のオプションのファイル/ディレクトリを含める」という質問項目について，なにも選択せず Enter キーを押す

以上の手順を実行すると，`.devcontainer` という名前のフォルダの中に Dev Container の構成ファイルである `devcontainer.json` が作成されます．ファイルの中身は次のようになっています．

```jsonc
// For format details, see https://aka.ms/devcontainer.json. For config options, see the
// README at: https://github.com/devcontainers/templates/tree/main/src/ubuntu
{
  "name": "Ubuntu",
  // Or use a Dockerfile or Docker Compose file. More info: https://containers.dev/guide/dockerfile
  "image": "mcr.microsoft.com/devcontainers/base:noble",

  // Features to add to the dev container. More info: https://containers.dev/features.
  // "features": {},

  // Use 'forwardPorts' to make a list of ports inside the container available locally.
  // "forwardPorts": [],

  // Use 'postCreateCommand' to run commands after the container is created.
  // "postCreateCommand": "uname -a",

  // Configure tool-specific properties.
  // "customizations": {},

  // Uncomment to connect as root instead. More info: https://aka.ms/dev-containers-non-root.
  // "remoteUser": "root"
}
```

## Dev Container で再度開く

Dev Container の構成ファイルができたら，次に Dev Container でプロジェクトを開きます．推奨する手順は次の通りです．

1. VS Code のウィンドウの左下にある「><」のアイコンをクリックする
2. 表示されたメニューの中から「コンテナーで再度開く」を選択する

しばらくすると Dev Container でプロジェクトが開きます．初回実行時は Docker イメージのダウンロードが走るためすこし時間がかかります．右下に表示される「開発コンテナーへの接続（ログの表示）」という通知をクリックすると，Dev Container の起動処理の進捗が確認できます．

## ターミナルからコマンドを実行する

Dev Container でプロジェクトが開いたら，ターミナルを開いてコマンドを実行してみましょう．推奨する手順は次の通りです．

1. VS Code のウィンドウの上部のメニューから「ターミナル > 新しいターミナル」を選択する
2. ターミナルが表示されたら，次のコマンドを入力して Enter キーを押す

```bash
uname -a
```

以下のような内容が表示されることを確認してください．

```bash
$ uname -a
Linux fcdeb5851797 6.6.87.2-microsoft-standard-WSL2 #1 SMP PREEMPT_DYNAMIC Thu Jun  5 18:30:46 UTC 2025 x86_64 x86_64 x86_64 GNU/Linux
```

以上で Dev Container のハンズオンは完了です．
