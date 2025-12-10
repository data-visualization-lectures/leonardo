


## ローカルでのビルド確認
 Netlify と同じ手順で動作を確認したい場合は、以下をルートディレクトリで実行してください。Parcel の依存関係（`deasync`）が利用するネイティブバイナリの都合で **Node.js 18 系（`18.20.4`）** と **Python 3.10 系** が必須です。`nvm` や `pyenv` / `mise` などのバージョンマネージャを使ってバージョンを切り替えてから実行してください。

| ステップ | コマンド例 |
|----------|------------|
| Node.js 18 を有効化 | `nvm use`（`nvm` 未使用の場合は公式バイナリ等で 18.20 系をインストールして PATH を切り替える） |
| Python 3.10 を有効化 | `pyenv install --skip-existing 3.10.14 && pyenv local 3.10.14`<br>または `mise use python@3.10` / `brew install python@3.10` 等で、`python3 --version` が 3.10.x になる状態にする |
| 依存関係のインストール | `yarn install` |
| 本番ビルドの生成 | `PYTHON="$(pyenv which python)" yarn --cwd packages/ui buildSite` など、`PYTHON` が **3.10.x** を指すように設定してから実行 |
| ビルド成果物の確認（任意） | `npx serve packages/ui/dist` |

`pyenv` を使用する場合は、`yarn config set python "$(pyenv which python)"` を実行して Yarn が 3.10 系の Python を参照するようにしてから `yarn install` を実行してください。

`packages/ui/dist` 以下が正しく生成され、ローカルサーバーが起動すれば本番ビルドが成功しています。
