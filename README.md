# Practice - uv

## Requirements

### Required

- [](#)

### Recommended

- [uv](https://docs.astral.sh/uv/)

## Logs

### Setup

```sh
# uv インストール
$ curl -LsSf https://astral.sh/uv/install.sh | sh

# uv, uvx コマンドが利用できることを確認する
$ uv --version
uv 0.9.7

$ uvx --version
uvx 0.9.7

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

# 仮想環境の作成 / Python 安定版のダウンロード
$ uv venv
Using CPython 3.12.3 interpreter at: /usr/bin/python3.12
Creating virtual environment at: .venv
Activate with: source .venv/bin/activate

# python3 の確認
$ python3 --version
Python 3.12.3

# 仮想環境を有効化する
$ source .venv/bin/activate

# 仮想環境が有効になっていることを確認
$ echo $VIRTUAL_ENV
/...略.../works/repos/dev/practice-uv/.venv

# 正常終了後、シェルが次の表示になっている
(practice-langgraph) ***@***:~/works/repos/dev/practice-langgraph [?main]
# ^^^^^^^^^^^^^^^^^^

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

# 仮想環境をオフにする
$ deactivate

# 正常終了後、シェルが次の表示になっている
***@***:~/works/repos/dev/practice-uv/.venv/bin
$
```

## References

- [astral-sh/uv: An extremely fast Python package and project manager, written in Rust.](https://github.com/astral-sh/uv)
- [langchain-ai/langgraph: Build resilient language agents as graphs.](https://github.com/langchain-ai/langgraph)
- [Pythonパッケージ管理 \[uv\] 完全入門 - Speaker Deck](https://speakerdeck.com/mickey_kubo/pythonpatukeziguan-li-uv-wan-quan-ru-men)
