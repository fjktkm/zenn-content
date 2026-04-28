---
title: "Git によるバージョン管理の設定"
---

## Git とは

Git は，ソフトウェア開発の現場で広く利用されているバージョン管理システムです．Git を使用することで，チーム開発を非同期で円滑に進めることができます．

## Git Feature の追加

`texlive/texlive` イメージには Git が含まれていません．コンテナ内で Git を使用できるようにするため，`devcontainer.json` に Git Feature を追加します．

```json
{
  "name": "LaTeX (TeX Live)",
  "image": "texlive/texlive:latest",
  "features": {
    "ghcr.io/devcontainers/features/common-utils:2": {},
    "ghcr.io/devcontainers/features/git:1": {}
  },
  "customizations": {
    "vscode": {
      "extensions": ["James-Yu.latex-workshop"]
    }
  }
}
```

`devcontainer.json` の編集が完了したら，コンテナをリビルドしてください．

## Git リポジトリの初期化

コンテナのリビルドが完了したら，次は Git リポジトリを初期化します．ターミナルで以下のコマンドを実行してください．

```bash
git init
```

## `.gitignore` を追加する

LaTeX ではコンパイル時に多数の中間ファイルが生成されます．これらをバージョン管理に含めると様々な問題が発生するため，通常は Git の管理対象から除外します．

Git には `.gitignore` に除外するファイルやディレクトリのパターンを記述することで，管理対象から除外する仕組みがあります．これを利用して，LaTeX の中間ファイルを除外します．

GitHub は各言語・環境向けの `.gitignore` テンプレートを公式に提供しています．ここでは，以下の `TeX.gitignore` を利用します．

https://github.com/github/gitignore/blob/main/TeX.gitignore

プロジェクトフォルダのルートに `.gitignore` というファイルを作成してください．ファイルの中身は，先ほどの `TeX.gitignore` の内容をコピペしてそのまま使えばよいです．これで LaTeX の中間ファイルが Git の管理対象から除外されます．

## `.gitattributes` を追加する

Windows と macOS・Linux では，テキストファイルの改行コードが異なります．そのため，ファイルを Dev Container を使わずに編集した場合などに，改行コードの違いによる問題が発生することがあります．

Git には `.gitattributes` にファイルごとの属性を記述することで Git の挙動を制御する仕組みがあります．これを利用して，改行コードの違いによる問題を回避します．

プロジェクトフォルダのルートに `.gitattributes` というファイルを作成してください．ファイルの中身は次のようにしてください．

```gitattributes
* text=auto eol=lf
*.{cmd,[cC][mM][dD]} text eol=crlf
*.{bat,[bB][aA][tT]} text eol=crlf
```

この設定により，改行コードの違いによる問題を回避できます．詳細については，以下のドキュメントを参照してください．

https://code.visualstudio.com/docs/devcontainers/tips-and-tricks

以上で Git によるバージョン管理の設定は完了です．
