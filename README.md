# レシートを登録するプログラム
## viteプロジェクトの作成 
[vite公式サイト](https://ja.vitejs.dev/guide/)

プロジェクトを作成
```sh
npm init vite@latest -y receipt2 -- --template vue
```

npm installして動作確認
```sh
cd receipt2
npm install
npm run dev
```
## firebase のセットアップ
ツールのインストール
```sh
npm install firebase
firebase init
# 対話形式で進むので、とりあえず以下を選択
? Which Firebase features do you want to set up for this directory? Press Space to select features, then Enter to confirm your choices.
(*) Firestore: Configure security rules and indexes files for Firestore
(*) Hosting: Configure files for Firebase Hosting and (optionally) set up GitHub Action deploys
(*) Hosting: Set up GitHub Action deploys
(*) Emulators: Set up local emulators for Firebase products
```
以下は不要なので削除する
```
./public/404.html
./public/index.html
```

## firebaseの設定
[vite公式のFireBase設定](https://ja.vitejs.dev/guide/static-deploy.html#google-firebase)

firebase.json
```json
{
  "hosting": {
    "public": "dist",
    "ignore": [],
    "rewrites": [
      {
        "source": "**",
        "destination": "/index.html"
      }
    ]
  }
}
```
.firebaserc(firebase init で既存プロジェクトを選択していれば設定済)
```js
{
  "projects": {
    "default": "<YOUR_FIREBASE_ID>"
  }
}
```

## Cypressでテスト

[Getting Started with Cypress Component Testing (Vue 2/3)](https://www.cypress.io/blog/2021/04/06/getting-start-with-cypress-component-testing-vue-2-3/)

[gitサンプル](https://github.com/cypress-io/cypress-component-examples)

[Qiitaの参考記事](https://qiita.com/t0daaay/items/c7fa204c30112ad6305e)

cypressのインストール
```sh
# これだと動かなかったので、サンプルのバージョンに合わせてインストール
# npm install cypress @cypress/vue@next @cypress/vite-dev-server --dev
npm install cypress@8.0.0 @cypress/vue@3.0.0-beta.3 @cypress/vite-dev-server@2.0.2 --dev
```

gitとかを参考に以下のファイルを作成する
- cypress/plugins/index.js
- cypress.json

あとはspec.jsをsrc/componentsに作成する

### CUI環境で実行するために必要な依存関係

[Cypress導入 - 詳細設定](https://docs.cypress.io/guides/continuous-integration/introduction#Dependencies)

```sh
# Ubuntu/Debian
apt-get install libgtk2.0-0 libgtk-3-0 libgbm-dev libnotify-dev libgconf-2-4 libnss3 libxss1 libasound2 libxtst6 xauth xvfb
# CentOS
yum install -y xorg-x11-server-Xvfb gtk2-devel gtk3-devel libnotify-devel GConf2 nss libXScrnSaver alsa-lib
```
