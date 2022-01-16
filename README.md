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
