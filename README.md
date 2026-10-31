# Python Default

uv + Ruff + mypy を組み合わせた Python プロジェクトのテンプレート。

- Python 3.13
- パッケージ管理:[uv](https://docs.astral.sh/uv/)
- リンター/フォーマッター:[Ruff](https://docs.astral.sh/ruff/)
- 静的型チェック:[mypy](https://mypy.readthedocs.io/)

## Setup

```bash
# 依存関係のインストール(.venvを作成)
uv sync
```

## 開発コマンド

```bash
# フォーマット
uv run ruff format

# リント
uv run ruff check .
uv run ruff check . -- fix #自動修正

# 型チェック
uv run mypy .

# 実行
uv run python main.py
```

## 構成

| パス | 内容 |
| --- | --- |
| `main.py` | エントリポイント |
| `pyproject.toml` | プロジェクト定義、Ruff/mypy 設定 |
| `.vscode/settings.json` | 保存時フォーマット·import整理、mypy 設定 |

### 設定のポイント

- Ruff:`F`/`E`/`W`/`I`/`D`/`UP`/`B`/`RUF`を有効化。docstringは Google style
  スクリプト用途向けに一部の`D`ルールと、日本語コメントを許容するため`RUF001`~`RUF003`を除外
- mypy:`warn_return_any`/`warn_unused_ignores`を有効、`ignore_missing_imports`で型スタブ未整備のライブラリを許容
- サブディレクトリをパッケージとして import する場合は、`pyproject.toml`の`[build-system]`/`[tool.hatch.build.targets.wheel]`のコメントを解除して使う

## 参考

[uv の使い方](https://note.com/npaka/n/n44c54312fb04)  
[Python開発環境をVSCode+uvで整える](https://qiita.com/ebimontblanc/items/8a0a52b10a82ba800ea5)
