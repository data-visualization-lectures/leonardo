# Leonardo

## 手順

### 環境設定
nvm use

### インストール
pyenv install --skip-existing 3.10.14 && pyenv local 3.10.14
yarn install

### ビルド
PYTHON="$(pyenv which python)" yarn --cwd packages/ui buildSite

### ローカル確認
npx serve packages/ui/dist -l 9000
http://localhost:9000/?auth_debug

`packages/ui/dist` 以下が正しく生成され、ローカルサーバーが起動すれば本番ビルドが成功しています。
