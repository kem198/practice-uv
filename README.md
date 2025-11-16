<!-- omit in toc -->
# Practice - uv

[uv](https://docs.astral.sh/uv/) をインストール ～ Hello World するまでのメモ。

加えて、仮想環境の有効化 / 無効化、ライブラリインストールなど。

<!-- omit in toc -->
## TOC

- [Runtime](#runtime)
- [Logs](#logs)
    - [uv のインストール](#uv-のインストール)
    - [アプリケーションの初期作成](#アプリケーションの初期作成)
    - [仮想環境の作成 / Python のインストール](#仮想環境の作成--python-のインストール)
    - [仮想環境を有効化する](#仮想環境を有効化する)
    - [Hello World](#hello-world)
    - [ライブラリのインストール](#ライブラリのインストール)
    - [仮想環境を無効化する](#仮想環境を無効化する)
- [References](#references)

## Runtime

- 実行環境: Ubuntu on WSL

    ```sh
    $ lsb_release -a
    No LSB modules are available.
    Distributor ID: Ubuntu
    Description:    Ubuntu 24.04.2 LTS
    Release:        24.04
    Codename:       noble
    ```

## Logs

上から順に実行した。

### uv のインストール

```sh
# 公式手順を基に uv をインストールする
# https://github.com/astral-sh/uv?tab=readme-ov-file#installation
$ curl -LsSf https://astral.sh/uv/install.sh | sh

# uv, uvx コマンドが利用できることを確認する
$ uv --version
uv 0.9.7

$ uvx --version
uvx 0.9.7
```

### アプリケーションの初期作成

```sh
# 練習用ディレクトリを作成・初期化
$ uv init practice-uv
Initialized project `practice-uv` at `/home/kenkenpa198/works/repos/dev/practice-uv`

# cd
cd practice-uv

# (任意) VS Code で開く
$ code .

# ファイルが作成されているので first commit する
$ git status -s
?? .gitignore
?? .python-version
?? README.md
?? main.py
?? pyproject.toml

$ git add -vA
add '.gitignore'
add '.python-version'
add 'README.md'
add 'main.py'
add 'pyproject.toml'

$ git commit -m 'first commit'
[main (root-commit) 541a94b] first commit
 5 files changed, 24 insertions(+)
 create mode 100644 .gitignore
 create mode 100644 .python-version
 create mode 100644 README.md
 create mode 100644 main.py
 create mode 100644 pyproject.toml
```

### 仮想環境の作成 / Python のインストール

```sh
# 仮想環境の作成 / Python 安定版のダウンロード
$ uv venv
Using CPython 3.12.3 interpreter at: /usr/bin/python3.12
Creating virtual environment at: .venv
Activate with: source .venv/bin/activate

# python3 が使えることを確認
$ python3 --version
Python 3.12.3
```

### 仮想環境を有効化する

```sh
# 仮想環境を有効化するコマンドを実行する
$ source .venv/bin/activate

# 仮想環境が有効になっていることを確認
$ echo $VIRTUAL_ENV
/...略.../works/repos/dev/practice-uv/.venv

# 正常終了後、シェルが次の表示になっている
(practice-langgraph) ***@***:~/works/repos/dev/practice-langgraph [?main]
# ^^^^^^^^^^^^^^^^^^
```

### Hello World

```sh
# main.py を実行
$ python3 main.py
Hello from practice-uv!
```

### ライブラリのインストール

```sh
# ライブラリ (例: langgraph ) をインストールする
$ uv add langgraph

# .toml ファイルとロックファイルができた
$ git status -s
 M pyproject.toml
?? uv.lock

# コミット
$ git add -vA
add 'pyproject.toml'
add 'uv.lock'

$ git commit -m 'run `uv add langgraph`'
[main 6b29672] run `uv add langgraph`
 2 files changed, 708 insertions(+), 1 deletion(-)
 create mode 100644 uv.lock
```

### 仮想環境を無効化する

```sh
# 仮想環境を無効化するコマンドを実行する
$ deactivate

# 正常終了後、シェルが次の表示になっている
***@***:~/works/repos/dev/practice-uv/.venv/bin
$
```

## References

- [astral-sh/uv: An extremely fast Python package and project manager, written in Rust.](https://github.com/astral-sh/uv)
- [langchain-ai/langgraph: Build resilient language agents as graphs.](https://github.com/langchain-ai/langgraph)
- [Pythonパッケージ管理 \[uv\] 完全入門 - Speaker Deck](https://speakerdeck.com/mickey_kubo/pythonpatukeziguan-li-uv-wan-quan-ru-men)
