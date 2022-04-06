---
ms.openlocfilehash: b8fb61f78cffb27cea5f313a39494fc0dfcdf7b3
ms.sourcegitcommit: 27a4afc732f8733e6022af2a58d01af5ae83545b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2022
ms.locfileid: "140813695"
---
このプロジェクトは、[Create React App](https://github.com/facebookincubator/create-react-app) を使用してブートストラップされました。

一般的なタスクの実行方法に関する情報を以下に示します。<br>
このガイドの最新バージョンは、[こちら](https://github.com/facebookincubator/create-react-app/blob/master/packages/react-scripts/template/README.md)を参照してください。

## <a name="table-of-contents"></a>目次

- [新しいリリースへの更新](#updating-to-new-releases)
- [フィードバックの送信](#sending-feedback)
- [フォルダー構造](#folder-structure)
- [使用可能なスクリプト](#available-scripts)
  - [npm start](#npm-start)
  - [npm test](#npm-test)
  - [npm run build](#npm-run-build)
  - [npm run eject](#npm-run-eject)
- [サポートされているブラウザー](#supported-browsers)
- [サポートされている言語機能とポリフィル](#supported-language-features-and-polyfills)
- [エディターでの構文の強調表示](#syntax-highlighting-in-the-editor)
- [エディターでの Lint 出力の表示](#displaying-lint-output-in-the-editor)
- [エディターでのデバッグ](#debugging-in-the-editor)
- [コードの自動的な書式設定](#formatting-code-automatically)
- [ページの変更`<title>`](#changing-the-page-title)
- [依存関係のインストール](#installing-a-dependency)
- [コンポーネントのインポート](#importing-a-component)
- [コードの分割](#code-splitting)
- [スタイルシートの追加](#adding-a-stylesheet)
- [CSS の後処理](#post-processing-css)
- [CSS プリプロセッサの追加 (Sass、Less など)](#adding-a-css-preprocessor-sass-less-etc)
- [イメージ、フォント、ファイルの追加](#adding-images-fonts-and-files)
- [`public` フォルダーの使用](#using-the-public-folder)
  - [HTML の変更](#changing-the-html)
  - [モジュール システムの外部へのアセットの追加](#adding-assets-outside-of-the-module-system)
  - [`public` フォルダーを使用する場合](#when-to-use-the-public-folder)
- [グローバル変数の使用](#using-global-variables)
- [ブートストラップの追加](#adding-bootstrap)
  - [カスタム テーマの使用](#using-a-custom-theme)
- [フローの追加](#adding-flow)
- [ルーターの追加](#adding-a-router)
- [カスタム環境変数の追加](#adding-custom-environment-variables)
  - [HTML での環境変数の参照](#referencing-environment-variables-in-the-html)
  - [ご利用のシェルへの一時環境変数の追加](#adding-temporary-environment-variables-in-your-shell)
  - [`.env` への開発環境変数の追加](#adding-development-environment-variables-in-env)
- [デコレーターを使用できますか?](#can-i-use-decorators)
- [AJAX 要求を使用したデータのフェッチ](#fetching-data-with-ajax-requests)
- [API バックエンドとの統合](#integrating-with-an-api-backend)
  - [Node](#node)
  - [Ruby on Rails](#ruby-on-rails)
- [開発時に API 要求をプロキシ経由にする](#proxying-api-requests-in-development)
  - [プロキシを構成した後の "無効なホスト ヘッダー" エラー](#invalid-host-header-errors-after-configuring-proxy)
  - [プロキシの手動構成](#configuring-the-proxy-manually)
  - [WebSocket プロキシの構成](#configuring-a-websocket-proxy)
- [開発での HTTPS の使用](#using-https-in-development)
- [サーバーでの動的 `<meta>` タグの生成](#generating-dynamic-meta-tags-on-the-server)
- [静的 HTML ファイルへのプリレンダリング](#pre-rendering-into-static-html-files)
- [サーバーからページへのデータの挿入](#injecting-data-from-the-server-into-the-page)
- [テストの実行](#running-tests)
  - [ファイル名の規則](#filename-conventions)
  - [コマンド ライン インターフェイス](#command-line-interface)
  - [バージョン コントロールの統合](#version-control-integration)
  - [テストの作成](#writing-tests)
  - [コンポーネントのテスト](#testing-components)
  - [サード パーティ アサーション ライブラリの使用](#using-third-party-assertion-libraries)
  - [テスト環境の初期化](#initializing-test-environment)
  - [テストのフォーカスと除外](#focusing-and-excluding-tests)
  - [カバレッジ レポート](#coverage-reporting)
  - [継続的インテグレーション](#continuous-integration)
  - [jsdom の無効化](#disabling-jsdom)
  - [スナップショット テスト](#snapshot-testing)
  - [エディターとの統合](#editor-integration)
- [テストのデバッグ](#debugging-tests)
  - [Chrome でのテストのデバッグ](#debugging-tests-in-chrome)
  - [Visual Studio Code でのテストのデバッグ](#debugging-tests-in-visual-studio-code)
- [コンポーネントを分離して開発](#developing-components-in-isolation)
  - [Storybook の概要](#getting-started-with-storybook)
  - [Styleguidist の概要](#getting-started-with-styleguidist)
- [npm へのコンポーネントの発行](#publishing-components-to-npm)
- [プログレッシブ Web アプリの作成](#making-a-progressive-web-app)
  - [キャッシュのオプトアウト](#opting-out-of-caching)
  - [オフラインファーストの考慮事項](#offline-first-considerations)
  - [プログレッシブ Web アプリ メタデータ](#progressive-web-app-metadata)
- [バンドル サイズの分析](#analyzing-the-bundle-size)
- [デプロイ](#deployment)
  - [静的サーバー](#static-server)
  - [他のソリューション](#other-solutions)
  - [クライアント側ルーティングを使用したアプリの提供](#serving-apps-with-client-side-routing)
  - [相対パスの構築](#building-for-relative-paths)
  - [Azure](#azure)
  - [Firebase](#firebase)
  - [GitHub ページ](#github-pages)
  - [Heroku](#heroku)
  - [Netlify](#netlify)
  - [Now](#now)
  - [S3 と CloudFront](#s3-and-cloudfront)
  - [Surge](#surge)
- [高度な構成](#advanced-configuration)
- [トラブルシューティング](#troubleshooting)
  - [`npm start` が変更を検出しない](#npm-start-doesnt-detect-changes)
  - [`npm test` が macOS Sierra でハングする](#npm-test-hangs-on-macos-sierra)
  - [`npm run build` が早期に終了する](#npm-run-build-exits-too-early)
  - [`npm run build` が Heroku で失敗する](#npm-run-build-fails-on-heroku)
  - [`npm run build` の縮小に失敗する](#npm-run-build-fails-to-minify)
  - [Moment.js ロケールがない](#momentjs-locales-are-missing)
- [Eject の代替手段](#alternatives-to-ejecting)
- [説明不足ですか。](#something-missing)

## <a name="updating-to-new-releases"></a>新しいリリースへの更新

Create React App は、次の 2 つのパッケージに分かれています。

* `create-react-app` は、新しいプロジェクトの作成に使用するグローバル コマンドライン ユーティリティです。
* `react-scripts` は、生成されたプロジェクト内の開発依存関係 (このプロジェクトも含む) です。

ほとんどの場合、`create-react-app` 自体を更新する必要はありません。これは、すべてのセットアップを `react-scripts` に委任します。

`create-react-app` を実行すると、常に最新バージョンの `react-scripts` でプロジェクトが作成されるため、新しく作成されたアプリのすべての新機能と改善点が自動的に取得されます。

既存のプロジェクトを新しいバージョンの `react-scripts` に更新するには、[changelog を開き](https://github.com/facebookincubator/create-react-app/blob/master/CHANGELOG.md)、現在使用しているバージョンを見つけて (不明な場合は、このフォルダーの `package.json` を確認します)、新しいバージョンの移行手順を適用します。

ほとんどの場合、`package.json` で `react-scripts` バージョンをバンプし、このフォルダーで `npm install` を実行するだけで十分ですが、破壊的変更の可能性については、[changelog](https://github.com/facebookincubator/create-react-app/blob/master/CHANGELOG.md) を参照することをお勧めします。

`react-scripts` を簡単にアップグレードできるように、破壊的変更を最小限に抑えることをお約束します。

## <a name="sending-feedback"></a>フィードバックの送信

[皆様からのフィードバック](https://github.com/facebookincubator/create-react-app/issues)をお待ちしております。

## <a name="folder-structure"></a>フォルダー構造

作成後、プロジェクトは次のようになります。

```
my-app/
  README.md
  node_modules/
  package.json
  public/
    index.html
    favicon.ico
  src/
    App.css
    App.js
    App.test.js
    index.css
    index.js
    logo.svg
```

プロジェクトをビルドするには、**次のファイルが正確なファイル名で存在する必要があります**。

* `public/index.html` は、ページ テンプレートで、
* `src/index.js` は、JavaScript のエントリ ポイントです。

他のファイルは削除することも、名前を変更することもできます。

`src` 内にサブディレクトリを作成することができます。 リビルドを迅速化するために、`src` 内のファイルのみが Webpack によって処理されます。<br>
**JS および CSS ファイルはすべて `src` 内に配置する必要があります**。そうしなければ、Webpack によって認識されません。

`public/index.html` から使用できるのは、`public` 内のファイルのみです。<br>
JavaScript および HTML の資産を使用するには、次の手順を参照してください。

ただし、より上位のディレクトリを作成することもできます。<br>
それらは運用ビルドには含まれていないため、ドキュメントなどに使用できます。

## <a name="available-scripts"></a>使用可能なスクリプト

プロジェクト ディレクトリでは、次のスクリプトを実行できます。

### `npm start`

開発モードでアプリを実行します。<br>
[http://localhost:3000](http://localhost:3000) を開くと、ブラウザーに表示されます。

編集を行うと、ページが再読み込みされます。<br>
また、コンソールには、lint エラーも表示されます。

### `npm test`

テスト ランナーを対話型ウォッチ モードで起動します。<br>
詳細については、[テストの実行](#running-tests)に関するセクションを参照してください。

### `npm run build`

運用環境用のアプリを `build` にビルドします。<br>
React を運用モードで正しくバンドルし、最良のパフォーマンスが得られるようにビルドを最適化します。

ビルドはミニファイ処理され、ファイル名にはハッシュが含まれます。<br>
アプリをデプロイする準備ができました。

詳細については、[デプロイ](#deployment) に関するセクションを参照してください。

### `npm run eject`

**注: これは一方向の操作です。`eject` を実行すると、戻ることはできません。**

ビルド ツールと構成の選択に問題がなければ、いつでも `eject` を実行できます。 このコマンドを実行すると、1 つのビルドの依存関係がプロジェクトから削除されます。

代わりに、すべての構成ファイルと推移的な依存関係 (Webpack、Babel、ESLint など) がプロジェクトに直接コピーされるので、それらを完全に制御できます。 `eject` を除くすべてのコマンドは引き続き機能しますが、それらはコピーされたスクリプトを参照するため、調整することができます。 これから先は、独自の作業になります。

`eject` を使用する必要はありません。 選別された機能セットは、中小規模のデプロイに適したものであり、この機能を使用する義務はありません。 ただし、準備が整ったときにカスタマイズできければ、このツールは役に立たないことがわかています。

## <a name="supported-browsers"></a>サポートされているブラウザー

生成されたプロジェクトでは、既定で、最新バージョンの React が使用されます。

サポートされているブラウザーの詳細については、[React のドキュメント](https://reactjs.org/docs/react-dom.html#browser-support)を参照してください。

## <a name="supported-language-features-and-polyfills"></a>サポートされている言語機能とポリフィル

このプロジェクトでは、最新の JavaScript 標準のスーパーセットがサポートされています。<br>
[ES6](https://github.com/lukehoban/es6features) 構文機能に加えて、次の機能もサポートされています。

* [指数演算子](https://github.com/rwaldron/exponentiation-operator) (ES2016)。
* [Async/await](https://github.com/tc39/ecmascript-asyncawait) (ES2017)。
* [Object Rest/Spread Properties](https://github.com/sebmarkbage/ecmascript-rest-spread) (ステージ 3 プロポーザル)。
* [Dynamic import()](https://github.com/tc39/proposal-dynamic-import) (ステージ 3 プロポーザル)
* [クラス フィールドと静的プロパティ](https://github.com/tc39/proposal-class-public-fields) (ステージ 2 プロポーザル)。
* [JSX](https://facebook.github.io/react/docs/introducing-jsx.html) および [Flow](https://flowtype.org/) 構文。

詳細については、[さまざまなプロポーザル ステージ](https://babeljs.io/docs/plugins/#presets-stage-x-experimental-presets-)を参照してください。

試験的なプロポーザルについては注意して使用することをお勧めしますが、Facebook では、製品コードでこれらの機能を多用しているため、将来これらのプロポーザルのいずれかが変更された場合は、[codemods](https://medium.com/@cpojer/effective-javascript-codemods-5a6686bb46fb) を提供する予定です。

**プロジェクトには、次に示す一部の ES6 [ポリフィル](https://wikipedia.org/wiki/Polyfill)** のみが含まれていることに注意してください。

* [`object-assign`](https://github.com/sindresorhus/object-assign) による [`Object.assign()`](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object/assign)。
* [`promise`](https://github.com/then/promise) による [`Promise`](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise)。
* [`whatwg-fetch`](https://github.com/github/fetch) による [`fetch()`](https://developer.mozilla.org/docs/Web/API/Fetch_API)。

**ランタイム サポート** を必要とする ES6 以降の他の機能 (`Array.from()` や `Symbol` など) を使用する場合は、必ず適切なポリフィルを手動で含めるか、または対象としているブラウザーが既にそれらをサポートしていることを確認してください。

また、`for...of` や `[...nonArrayValue]` などの一部の新しい構文機能を使用すると、Babel では、ES6 ランタイム機能に依存するコードが出力され、ポリフィルなしでは動作しない可能性があります。 不明な場合は、[Babel REPL](https://babeljs.io/repl/) を使用して、特定の構文がどのようにコンパイルされるかを確認してください。

## <a name="syntax-highlighting-in-the-editor"></a>エディターでの構文の強調表示

好みのテキスト エディターでの構文の強調表示を構成するには、[Babel ドキュメントの関連するページ](https://babeljs.io/docs/editors)に移動し、その手順に従います。 最も一般的なエディターの一部について説明されています。

## <a name="displaying-lint-output-in-the-editor"></a>エディターでの lint 出力の表示

>注: この機能は、`react-scripts@0.2.0` 以降で使用できます。<br>
>また、npm 3 以降でのみ機能します。

Sublime Text、Atom、Visual Studio Code などの一部のエディターでは、ESLint のプラグインが提供されています。

これらは、リンティングには必要ありません。 リンター出力は、端末とブラウザー コンソールに直接表示されます。 ただし、lint 結果をエディターに直接表示したい場合は、実行できるいくつかの追加手順があります。

最初に、エディター用の ESLint プラグインをインストールする必要があります。 次に、`.eslintrc` という名前のファイルをプロジェクト ルートに追加します。

```js
{
  "extends": "react-app"
}
```

以上で、エディターにリンティング警告が表示されます。

`.eslintrc` ファイルをさらに編集しても、これらの変更は、**エディター統合にのみ影響する** ことに注意してください。 端末やブラウザー内の lint 出力には影響しません。 これは、Create React App では、一般的なエラーを検出する最小限のルール セットが意図的に提供されるためです。

プロジェクトのコーディング スタイルを適用する場合は、ESLint スタイル ルールの代わりに [Prettier](https://github.com/jlongster/prettier) を使用することを検討してください。

## <a name="debugging-in-the-editor"></a>エディターでのデバッグ

**この機能は現在、[Visual Studio Code](https://code.visualstudio.com) および [WebStorm](https://www.jetbrains.com/webstorm/) でのみサポートされています。**

Visual Studio Code および WebStorm では、Create React App ですぐに使用できるデバッグがサポートされています。 これにより、開発者はエディターを離れることなく React コードを記述およびデバッグできます。最も重要なことは、ツールを切り替える必要がないため、コンテキストの切り替えが最小限で済む継続的な開発ワークフローを実現できることです。

### <a name="visual-studio-code"></a>Visual Studio Code

最新バージョンの [VS Code](https://code.visualstudio.com) と VS Code [Chrome デバッガー拡張機能](https://marketplace.visualstudio.com/items?itemName=msjsdiag.debugger-for-chrome)がインストールされている必要があります。

次に、以下のブロックを `launch.json` ファイルに追加し、アプリのルート ディレクトリの `.vscode` フォルダー内に配置します。

```json
{
  "version": "0.2.0",
  "configurations": [{
    "name": "Chrome",
    "type": "chrome",
    "request": "launch",
    "url": "http://localhost:3000",
    "webRoot": "${workspaceRoot}/src",
    "userDataDir": "${workspaceRoot}/.vscode/chrome",
    "sourceMapPathOverrides": {
      "webpack:///src/*": "${webRoot}/*"
    }
  }]
}
```
>注: [HOST または PORT 環境変数](#advanced-configuration) を使用して調整を行った場合、URL が異なることがあります。

`npm start` を実行してアプリを起動し、`F5` キーを押すか、緑色のデバッグ アイコンをクリックして、VS Code でデバッグを開始します。 以上で、コードの記述、ブレークポイントの設定、コードの変更、新しく変更されたコードのデバッグをすべてエディターから行うことができます。

### <a name="webstorm"></a>WebStorm

[WebStorm](https://www.jetbrains.com/webstorm/) と [JetBrains IDE サポート](https://chrome.google.com/webstore/detail/jetbrains-ide-support/hmhgeddbohgjknpmjagkdomcpobmllji) Chrome 拡張機能がインストールされている必要があります。

WebStorm メニュー `Run` で、`Edit Configurations...` を選択します。 次に、`+` をクリックして、`JavaScript Debug` を選択します。 `http://localhost:3000` を URL フィールドに貼り付けて、構成を保存します。

>注: [HOST または PORT 環境変数](#advanced-configuration) を使用して調整を行った場合、URL が異なることがあります。

`npm start` を実行してアプリを起動し、macOS では `^D` キー、Windows と Linux では `F9` キーを押すか、または緑色のデバッグ アイコンをクリックして、WebStorm でのデバッグを開始します。

IntelliJ IDEA Ultimate、PhpStorm、PyCharm Pro、および RubyMine でアプリケーションをデバッグするのと同じ方法です。 

## <a name="formatting-code-automatically"></a>コードの自動的な書式設定

Prettier は、JavaScript、CSS、および JSON をサポートする、こだわりのあるコード フォーマッタです。 Prettier を使用すると、記述するコードを自動的に書式設定して、プロジェクト内のコード スタイルを保証できます。 詳細については、[Prettier の GitHub ページ](https://github.com/prettier/prettier)を参照し、この[ページで動作していることを確認](https://prettier.github.io/prettier/)してください。

git でコミットを行うたびにコードを書式設定するには、次の依存関係をインストールする必要があります。

```sh
npm install --save husky lint-staged prettier
```

`yarn` を使用することもできます。

```sh
yarn add husky lint-staged prettier
```

* `husky` では、npm スクリプトのように githooks を簡単に使用できます。
* `lint-staged` を使用すると、git でステージングされたファイルに対してスクリプトを実行できます。 詳細については、この [lint-staged に関するブログ投稿](https://medium.com/@okonetchnikov/make-linting-great-again-f3890e1ad6b8)を参照してください。
* `prettier` は、コミットの前に実行する JavaScript フォーマッタです。

プロジェクト ルートの `package.json` に数行を追加することで、すべてのファイルが正しく書式設定されるようになりました。

次の行を `scripts` セクションに追加します。

```diff
  "scripts": {
+   "precommit": "lint-staged",
    "start": "react-scripts start",
    "build": "react-scripts build",
```

次に、"lint-staged" フィールドを `package.json` に追加します。次に例を示します。

```diff
  "dependencies": {
    // ...
  },
+ "lint-staged": {
+   "src/**/*.{js,jsx,json,css}": [
+     "prettier --single-quote --write",
+     "git add"
+   ]
+ },
  "scripts": {
```

これで、Prettier ではコミットを行うたびに、変更されたファイルが自動的に書式設定されます。 初回の場合、`./node_modules/.bin/prettier --single-quote --write "src/**/*.{js,jsx,json,css}"` を実行して、プロジェクト全体の書式を設定することもできます。

次に、お気に入りのエディターで Prettier を統合することをお勧めします。 Prettier GitHub ページの[エディター統合](https://prettier.io/docs/en/editors.html)に関するセクションを参照してください。

## <a name="changing-the-page-title"></a>ページ `<title>` の変更

生成されたプロジェクトの `public` フォルダーに、ソース HTML ファイルがあります。 その中の `<title>` タグを編集して、タイトルを "React App" から他のものに変更することができます。

通常、`public` フォルダー内のファイルは頻繁に編集しないことに注意してください。 たとえば、[スタイルシートの追加](#adding-a-stylesheet)は、HTML に触ることなく行われます。

コンテンツに基づいてページ タイトルを動的に更新する必要がある場合は、ブラウザー [`document.title`](https://developer.mozilla.org/docs/Web/API/Document/title) API を使用できます。 React コンポーネントからタイトルを変更する、より複雑なシナリオでは、サード パーティのライブラリである [React Helmet](https://github.com/nfl/react-helmet) を使用できます。

運用環境でアプリ用にカスタム サーバーを使用していて、ブラウザーに送信される前にタイトルを変更する場合は、[このセクション](#generating-dynamic-meta-tags-on-the-server)のアドバイスに従うことができます。 または、各ページを静的 HTML ファイルとして事前にビルドして、JavaScript バンドルを読み込むこともできます。これについては、[こちら](#pre-rendering-into-static-html-files)を参照してください。

## <a name="installing-a-dependency"></a>依存関係のインストール

生成されたプロジェクトには、依存関係として React と ReactDOM が含まれます。 また、開発の依存関係として Create React App で使用される一連のスクリプトも含まれています。 `npm` を使用して、他の依存関係 (React Router など) をインストールすることができます。

```sh
npm install --save react-router
```

`yarn` を使用することもできます。

```sh
yarn add react-router
```

これは、`react-router` だけでなく、すべてのライブラリに対して機能します。

## <a name="importing-a-component"></a>コンポーネントのインポート

このプロジェクトのセットアップでは、Babel のおかげで ES6 モジュールがサポートされています。<br>
`require()` と `module.exports` を使用することもできますが、代わりに [`import` と `export`](http://exploringjs.com/es6/ch_modules.html) を使用することをお勧めします。

次に例を示します。

### `Button.js`

```js
import React, { Component } from 'react';

class Button extends Component {
  render() {
    // ...
  }
}

export default Button; // Don’t forget to use export default!
```

### `DangerButton.js`


```js
import React, { Component } from 'react';
import Button from './Button'; // Import a component from another file

class DangerButton extends Component {
  render() {
    return <Button color="red" />;
  }
}

export default DangerButton;
```

[既定のエクスポートと名前付きエクスポートの違い](http://stackoverflow.com/questions/36795819/react-native-es-6-when-should-i-use-curly-braces-for-import/36796281#36796281)に注意してください。 これは間違いの一般的な原因です。

モジュールが 1 つのもの (コンポーネントなど) のみをエクスポートする場合は、既定のインポートとエクスポートを使用することをお勧めします。 これは、`export default Button` および `import Button from './Button'` を使用するときに取得するものです。

名前付きエクスポートは、いくつかの関数をエクスポートするユーティリティ モジュールに便利です。 モジュールには、最大で 1 つの既定のエクスポートと、任意の数の名前付きエクスポートを含めることができます。

ES6 モジュールの詳細については、次を参照してください。

* [中かっこを使用する場合](http://stackoverflow.com/questions/36795819/react-native-es-6-when-should-i-use-curly-braces-for-import/36796281#36796281)
* [ES6 の探索: モジュール](http://exploringjs.com/es6/ch_modules.html)
* [ES6 について: モジュール](https://leanpub.com/understandinges6/read#leanpub-auto-encapsulating-code-with-modules)

## <a name="code-splitting"></a>コードの分割

コードの分割を使用すると、使用する前にユーザーがアプリ全体をダウンロードするのではなく、コードを小さいチャンクに分割し、必要に応じて読み込むことができます。

このプロジェクトのセットアップでは、[動的 `import()`](http://2ality.com/2017/01/import-operator.html#loading-code-on-demand) によるコードの分割がサポートされています。 この[提案](https://github.com/tc39/proposal-dynamic-import)はステージ 3 にあります。 `import()` の関数のような形式で、モジュール名を引数として受け取り、常にモジュールの名前空間オブジェクトに解決される [`Promise`](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise) を返します。

たとえば次のようになります。

### `moduleA.js`

```js
const moduleA = 'Hello';

export { moduleA };
```
### `App.js`

```js
import React, { Component } from 'react';

class App extends Component {
  handleClick = () => {
    import('./moduleA')
      .then(({ moduleA }) => {
        // Use moduleA
      })
      .catch(err => {
        // Handle failure
      });
  };

  render() {
    return (
      <div>
        <button onClick={this.handleClick}>Load</button>
      </div>
    );
  }
}

export default App;
```

これにより、`moduleA.js` とそのすべての固有の依存関係が個別のチャンクとして作成され、ユーザーが [読み込み] ボタンをクリックした後にのみ読み込みを行います。

また、`async` / `await` 構文と共に使用することもできます。

### <a name="with-react-router"></a>React Router を使用する

React Router を使用している場合は、それを使用してコードの分割を使用する方法について[このチュートリアル](http://serverless-stack.com/chapters/code-splitting-in-create-react-app.html)を確認してください。 関連する GitHub リポジトリは[こちら](https://github.com/AnomalyInnovations/serverless-stack-demo-client/tree/code-splitting-in-create-react-app)にあります。

また、React のドキュメントの[コードの分割](https://reactjs.org/docs/code-splitting.html)に関するセクションもご覧ください。

## <a name="adding-a-stylesheet"></a>スタイルシートの追加

このプロジェクトのセットアップでは、すべてのアセットを処理するために [Webpack](https://webpack.js.org/) を使用します。 Webpack では、JavaScript 以外の `import` 概念を "拡張" する独自の方法を提供します。 JavaScript ファイルが CSS ファイルに依存していることを表現するには、**JavaScript ファイルから CSS をインポート** する必要があります。

### `Button.css`

```css
.Button {
  padding: 20px;
}
```

### `Button.js`

```js
import React, { Component } from 'react';
import './Button.css'; // Tell Webpack that Button.js uses these styles

class Button extends Component {
  render() {
    // You can use them as regular CSS styles
    return <div className="Button" />;
  }
}
```

**これは React には必要ありません** が、多くの方にとってこの機能は便利です。 このアプローチの利点については、[こちら](https://medium.com/seek-ui-engineering/block-element-modifying-your-javascript-components-d7f99fcab52b)を参照してください。 ただし、これにより、コードが Webpack 以外の他のビルド ツールおよび環境に移植しにくくなることに注意する必要があります。

開発では、このように依存関係を表現することで、編集時にスタイルをその場で再読み込みできるようにします。 運用環境では、すべての CSS ファイルが、ビルド出力で 1 つの縮小された `.css` ファイルに連結されます。

Webpack 固有のセマンティクスの使用を検討している場合は、すべての CSS を `src/index.css` に配置できます。 これは `src/index.js` からインポートされますが、後で別のビルド ツールに移行する場合は、そのインポートをいつでも削除できます。

## <a name="post-processing-css"></a>CSS の後処理

このプロジェクトのセットアップにより、CSS が縮小され、[Autoprefixer](https://github.com/postcss/autoprefixer) によって自動的にベンダー プレフィックスが追加されるため、心配する必要はありません。

次に例を示します。

```css
.App {
  display: flex;
  flex-direction: row;
  align-items: center;
}
```

これを次のようにします。

```css
.App {
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-orient: horizontal;
  -webkit-box-direction: normal;
      -ms-flex-direction: row;
          flex-direction: row;
  -webkit-box-align: center;
      -ms-flex-align: center;
          align-items: center;
}
```

何らかの理由で自動プレフィックスを無効にする必要がある場合は、[このセクションに従ってください](https://github.com/postcss/autoprefixer#disabling)。

## <a name="adding-a-css-preprocessor-sass-less-etc"></a>CSS プリプロセッサの追加 (SASS、Less など)

通常は、異なるコンポーネント間で同じ CSS クラスを再利用しないことをお勧めします。 たとえば、`<AcceptButton>` および `<RejectButton>` コンポーネントで `.Button` CSS クラスを使用するのではなく、独自の `.Button` のスタイルを持つ `<Button>` コンポーネント (`<AcceptButton>` と `<RejectButton>` の両方をレンダリングできる ([継承はできません](https://facebook.github.io/react/docs/composition-vs-inheritance.html))) を作成することをお勧めします。

多くの場合、この規則に従うと、mixin や入れ子などの機能がコンポーネント構成に置き換えられるため、CSS プリプロセッサがあまり役に立たなくなります。 しかし、必要な場合は、CSS プリプロセッサを統合することもできます。 このチュートリアルでは、SASS を使用しますが、Less、または別の方法を使用することもできます。

まず、SASS 用のコマンドライン インターフェイスをインストールしましょう。

```sh
npm install --save node-sass-chokidar
```

`yarn` を使用することもできます。

```sh
yarn add node-sass-chokidar
```

次に `package.json` で、次の行を `scripts` に追加します。

```diff
   "scripts": {
+    "build-css": "node-sass-chokidar src/ -o src/",
+    "watch-css": "npm run build-css && node-sass-chokidar src/ -o src/ --watch --recursive",
     "start": "react-scripts start",
     "build": "react-scripts build",
     "test": "react-scripts test --env=jsdom",
```

>注: 別のプリプロセッサを使用するには、`build-css` と `watch-css` コマンドをプリプロセッサのドキュメントに従って置き換えます。

これで、`src/App.css` の名前を `src/App.scss` に変更し、`npm run watch-css` を実行できるようになりました。 ウォッチャーは、`src` サブディレクトリ内のすべての SASS ファイルを検索し、その横に対応する CSS ファイルを作成します。ここでは、`src/App.css` を上書きします。 `src/App.js` では引き続き `src/App.css` がインポートされるため、スタイルはアプリケーションの一部になります。 これで `src/App.scss` を編集できるようになり、`src/App.css` が再生成されます。

SASS ファイル間で変数を共有するには、SASS インポートを使用します。 たとえば、`src/App.scss` やその他のコンポーネント スタイル ファイルには、変数の定義を持つ `@import "./shared.scss";` を含めることができます。

相対パスを使用せずにファイルをインポートできるようにするには、`package.json` のコマンドに `--include-path` オプションを追加します。

```
"build-css": "node-sass-chokidar --include-path ./src --include-path ./node_modules src/ -o src/",
"watch-css": "npm run build-css && node-sass-chokidar --include-path ./src --include-path ./node_modules src/ -o src/ --watch --recursive",
```

これにより、次のようなインポートを実行できます。

```scss
@import 'styles/_colors.scss'; // assuming a styles directory under src/
@import 'nprogress/nprogress'; // importing a css file from the nprogress node module
```

この時点で、ソース管理からすべての CSS ファイルを削除し、`.gitignore` ファイルに `src/**/*.css` を追加することができます。 一般に、ソース管理の外部にビルド製品を保持することをお勧めします。

最後の手順として、`npm start` を使用して `watch-css` を自動的に実行し、`npm run build` の一部として `build-css` を実行すると便利な場合があります。 `&&` 演算子を使用すると、2 つのスクリプトを順番に実行できます。 ただし、2 つのスクリプトを並列実行するクロスプラットフォームの方法はないため、次のようにパッケージをインストールします。

```sh
npm install --save npm-run-all
```

または、`yarn` を使用することもできます。

```sh
yarn add npm-run-all
```

次に、`start` と `build` スクリプトを変更して、CSS プリプロセッサ コマンドを含めることができます。

```diff
   "scripts": {
     "build-css": "node-sass-chokidar src/ -o src/",
     "watch-css": "npm run build-css && node-sass-chokidar src/ -o src/ --watch --recursive",
-    "start": "react-scripts-ts start",
-    "build": "react-scripts-ts build",
+    "start-js": "react-scripts-ts start",
+    "start": "npm-run-all -p watch-css start-js",
+    "build": "npm run build-css && react-scripts-ts build",
     "test": "react-scripts test --env=jsdom",
     "eject": "react-scripts eject"
   }
```

これで、`npm start` と `npm run build` を実行すると、SASS ファイルもビルドされます。

**なぜ `node-sass-chokidar` なのか**

`node-sass` は、次の問題があると報告されています。

- `node-sass --watch` は、仮想マシンまたは docker で使用されるときに、特定の条件で "パフォーマンスの問題" が発生することが報告されています。

- 無限スタイル コンパイル [#1939](https://github.com/facebookincubator/create-react-app/issues/1939)

- `node-sass` は、ディレクトリ内の新しいファイルを検出する際に問題があると報告されています [#1891](https://github.com/sass/node-sass/issues/1891)

 ここでは、これらの問題に対処するために `node-sass-chokidar` を使用します。

## <a name="adding-images-fonts-and-files"></a>イメージ、フォント、ファイルの追加

Webpack では、イメージやフォントなどの静的なアセットを CSS と同様に使用できます。

**TypeScript モジュールでファイル権限を `import` できます** 。 これにより、そのファイルがバンドルに含まれることが Webpack に伝えられます。 CSS インポートとは異なり、ファイルをインポートすると、文字列値が得られます。 この値は、コード内で参照できる最終的なパスです。たとえば、イメージの `src` 属性や PDF へのリンクの `href` などです。

サーバーへの要求の数を減らすために、1 万バイト未満のイメージをインポートすると、パスではなく [データ URI](https://developer.mozilla.org/docs/Web/HTTP/Basics_of_HTTP/Data_URIs) が返されます。 これは、次のファイル拡張子に適用されます: bmp、gif、jpg、jpeg、および png。 [#1153](https://github.com/facebookincubator/create-react-app/issues/1153) のため、SVG ファイルは除外されます。

作業を開始する前に、有効なモジュール形式として各アセットの種類を定義する必要があります。 それ以外の場合は、TypeScript コンパイラによって次のようなエラーが生成されます。

>モジュール './logo.png' が見つかりません。

TypeScript でアセット ファイルをインポートするには、プロジェクトに新しい型定義ファイルを作成し、`assets.d.ts` という名前を付けます。 次に、インポートする必要があるアセットの種類ごとに行を追加します。

```ts
declare module "*.gif";
declare module "*.jpg";
declare module "*.jpeg";
declare module "*.png";
declare module "*.svg";
```
(変更を有効にするには、コンパイラを再起動する必要があります)

この例では、有効なモジュール形式として、いくつかのイメージ ファイル拡張子を追加しました。

コンパイラが構成されたので、次にイメージ ファイルをインポートする例を示します。

```js
import React from 'react';
import logo from './logo.svg'; // Tell Webpack this JS file uses this image

console.log(logo); // /logo.84287d09.png

function Header() {
  // Import result is the URL of your image
  return <img src={logo} alt="Logo" />;
}

export default Header;
```

これにより、プロジェクトがビルドされるときに、Webpack によってイメージがビルド フォルダーに正しく移動され、正しいパスが提供されるようになります。

これは CSS でも動作します。

```css
.Logo {
  background-image: url(./logo.png);
}
```

Webpack は、CSS 内のすべての相対モジュール参照 (`./` で始まる) を検索し、コンパイルされたバンドルの最終的なパスに置き換えます。 入力を誤ったり、誤って重要なファイルを削除したりすると、存在しない JavaScript モジュールをインポートする場合と同様に、コンパイル エラーが表示されます。 コンパイル済みバンドルの最終的なファイル名は、コンテンツ ハッシュからの Webpack によって生成されます。 今後、ファイルの内容が変更された場合、Webpack では、運用環境で別の名前を指定するため、アセットの長期的なキャッシュについて心配する必要はありません。

これは Webpack のカスタム機能でもあることに注意してください。

**React には必要ありません** が、多くの人がその機能を利用しています (React Native ではイメージに同様のメカニズムを使用します)。<br>
静的アセットを処理する別の方法については、次のセクションで説明します。

## <a name="using-the-public-folder"></a>`public` フォルダーの使用

>注: この機能は、`react-scripts@0.5.0` 以降で使用できます。

### <a name="changing-the-html"></a>HTML の変更

`public` フォルダーには HTML ファイルが含まれており、これを調整して [ページ タイトルを設定](#changing-the-page-title)することができます。
コンパイルされたコードの `<script>` タグは、ビルド処理中に自動的に追加されます。

### <a name="adding-assets-outside-of-the-module-system"></a>モジュール システムの外部へのアセットの追加

`public` フォルダーに他のアセットを追加することもできます。

通常は、代わりに JavaScript ファイルにアセットを `import` することをお勧めします。
たとえば、[スタイルシートの追加](#adding-a-stylesheet)と[イメージとフォントの追加](#adding-images-fonts-and-files)に関するセクションを参照してください。
このメカニズムには、次のようなさまざまな利点があります。

* 余分なネットワーク要求を避けるために、スクリプトとスタイル シートが縮小され、バンドルされています。
* ファイルが見つからないと、ユーザーに対して 404 エラーではなくコンパイル エラーが表示されます。
* 結果のファイル名にはコンテンツ ハッシュが含まれているため、古いバージョンをキャッシュするブラウザーについて心配する必要はありません。

ただし、モジュール システムの外部にアセットを追加するために使用できる **エスケープ ハッチ** があります。

`public` フォルダーにファイルを配置した場合、ファイルは Webpack によって処理され **ません**。 代わりに、そのままビルド フォルダーにコピーされます。   `public` フォルダー内のアセットを参照するには、`PUBLIC_URL` という特殊な変数を使用する必要があります。

`index.html` の内部では、次のように使用できます。

```html
<link rel="shortcut icon" href="%PUBLIC_URL%/favicon.ico">
```

`%PUBLIC_URL%` プレフィックスでアクセスできるのは、`public` フォルダー内のファイルだけです。 `src` または `node_modules` のファイルを使用する必要がある場合は、このファイルをそこにコピーして、このファイルをビルドの一部にすることを明示的に指定する必要があります。

`npm run build` を実行すると、Create React App では `%PUBLIC_URL%` を正しい絶対パスに置き換えるので、クライアント側のルーティングを使用する場合や、ルート以外の URL でホストする場合でも、プロジェクトは動作します。

JavaScript コードでは、次のような目的で `process.env.PUBLIC_URL` を使用できます。

```js
render() {
  // Note: this is an escape hatch and should be used sparingly!
  // Normally we recommend using `import` for getting asset URLs
  // as described in “Adding Images and Fonts” above this section.
  return <img src={process.env.PUBLIC_URL + '/img/logo.png'} />;
}
```

このアプローチの欠点に留意してください。

* `public` フォルダー内のファイルは、後処理または縮小されません。
* 見つからないファイルはコンパイル時に呼び出されず、ユーザーに対して 404 エラーが表示されます。
* 結果のファイル名にコンテンツ ハッシュは含まれないため、クエリ引数が変更されるたびに、クエリ引数を追加するか、その名前を変更する必要があります。

### <a name="when-to-use-the-public-folder"></a>`public` フォルダーを使用する場合

通常は、[スタイルシート](#adding-a-stylesheet)、[イメージ、およびフォント](#adding-images-fonts-and-files)を JavaScript からインポートすることをお勧めします。
`public` フォルダーは、あまり一般的でないいくつかのケースの回避策として役立ちます。

* [`manifest.webmanifest`](https://developer.mozilla.org/docs/Web/Manifest) など、ビルド出力に特定の名前のファイルが必要である。
* 数千のイメージがあり、そのパスを動的に参照する必要がある。
* バンドルされているコードの外部にある [`pace.js`](http://github.hubspot.com/pace/docs/welcome/) のような小さなスクリプトを含める必要がある。
* 一部のライブラリが Webpack と互換性がない可能性があります。その場合、それを `<script>` タグとして含めるしかありません。

グローバル変数を宣言する `<script>` を追加する場合は、その使用方法に関する次のセクションも読む必要があります。

## <a name="using-global-variables"></a>グローバル変数の使用

グローバル変数を定義するスクリプトを HTML ファイルに含め、これらの変数のいずれかをコードで使用しようとすると、リンターは変数の定義を認識できないため、エラーが発生します。

このことを回避するには、次のように、`window` オブジェクトからグローバル変数を明示的に読み取ります。

```js
const $ = window.$;
```

これにより、入力ミスのためではなく、グローバル変数を意図的に使用していることが明らかになります。

または、その後に `// eslint-disable-line` を追加することで、すべての行を無視するようにリンターに強制することもできます。

## <a name="adding-bootstrap"></a>ブートストラップの追加

[React Bootstrap](https://react-bootstrap.github.io) を React と一緒に使用する必要はありませんが、これは Bootstrap を React アプリに統合するための一般的なライブラリです。 必要に応じて、次の手順に従って Create React App と統合できます。

npm から React Bootstrap と Bootstrap をインストールします。 React Bootstrap には Bootstrap CSS が含まれていないため、これもインストールする必要があります。

```sh
npm install --save react-bootstrap bootstrap@3
```

`yarn` を使用することもできます。

```sh
yarn add react-bootstrap bootstrap@3
```

```src/index.js``` ファイルの先頭に Bootstrap CSS と、必要に応じて Bootstrap テーマ CSS をインポートします。

```js
import 'bootstrap/dist/css/bootstrap.css';
import 'bootstrap/dist/css/bootstrap-theme.css';
// Put any other imports below so that CSS from your
// components takes precedence over default styles.
```

インポートには、```src/App.js``` ファイルまたはカスタム コンポーネント ファイル内の React Bootstrap コンポーネントが必要です。

```js
import { Navbar, Jumbotron, Button } from 'react-bootstrap';
```

これで、render メソッドで定義されているコンポーネント階層内で、インポートされた React Bootstrap コンポーネントを使用できるようになりました。 これは、React Bootstrap を使用して [`App.js`](https://gist.githubusercontent.com/gaearon/85d8c067f6af1e56277c82d19fd4da7b/raw/6158dd991b67284e9fc8d70b9d973efe87659d72/App.js) の再実行の例です。

### <a name="using-a-custom-theme"></a>カスタム テーマの使用

場合によっては、Bootstrap (または同等のパッケージ) の視覚スタイルを調整する必要があります。<br>
次の方法を提案します。

* Bootstrap など、カスタマイズするパッケージに依存する新しいパッケージを作成します。
* 必要なビルド ステップを追加して、テーマを調整し、npm でパッケージを発行します。
* アプリの依存関係として、独自のテーマ npm パッケージをインストールします。

次に、これらの手順に従って[カスタマイズされた Bootstrap](https://medium.com/@tacomanator/customizing-create-react-app-aa9ffb88165) を追加する例を示します。

## <a name="adding-flow"></a>Flow の追加

Flow は、バグの少ないコードを記述するのに役立つ静的型チェッカーです。 この概念が初めての場合は、[JavaScript での静的な型の使用](https://medium.com/@preethikasireddy/why-use-static-types-in-javascript-part-1-8382da1e0adb)に関するこの概要を確認してください。

最新バージョンの [Flow](http://flowtype.org/) は、Create React App ですぐに使用できます。

Create React App プロジェクトに Flow を追加するには、次の手順を実行します。

1. `npm install --save flow-bin` (または `yarn add flow-bin`) を実行します。
2. `package.json` の `scripts` セクションに `"flow": "flow"` を追加します。
3. `npm run flow init` (または `yarn flow init`) を実行して、ルート ディレクトリに [`.flowconfig` ファイル](https://flowtype.org/docs/advanced-configuration.html)を作成します。
4. 型チェックを実行する任意のファイル (たとえば、`// @flow` に) `src/App.js` を追加します。

以上で、`npm run flow` (または `yarn flow`) を実行し、ファイルを調べて型エラーの有無を確認できます。
必要に応じて、[Nuclide](https://nuclide.io/docs/languages/flow/) などの IDE を使用して、統合されたエクスペリエンスを向上させることもできます。
今後、これを Create React App にさらに緊密に統合する予定です。

Flow の詳細については、[Flow のドキュメント](https://flowtype.org/)を参照してください。

## <a name="adding-a-router"></a>ルーターの追加

Create React App では、特定のルーティング ソリューションについて規定されていませんが、[React Router](https://reacttraining.com/react-router/) が最も一般的です。

これを追加するには、次のスクリプトを実行します。

```sh
npm install --save react-router-dom
```

または、`yarn` を使用することもできます。

```sh
yarn add react-router-dom
```

これを試すには、`src/App.js` 内のすべてのコードを削除し、その Web サイトにあるいずれかの例に置き換えます。 [Basic Example](https://reacttraining.com/react-router/web/example/basic) は、始めるのに適しています。

アプリをデプロイする前に、[クライアント側のルーティングをサポートするように運用サーバーを構成することが必要な場合がある](#serving-apps-with-client-side-routing)ことに注意してください。

## <a name="adding-custom-environment-variables"></a>カスタム環境変数の追加

>注: この機能は、`react-scripts@0.2.3` 以降で使用できます。

プロジェクトでは、JS ファイルでローカルに宣言された場合と同様に、お使いの環境で宣言された変数を使用することができます。 既定では、`NODE_ENV` と、`REACT_APP_` で始まるその他の環境変数が定義されます。

**環境変数は、ビルド時に埋め込まれます**。 Create React App では静的な HTML、CSS、JS バンドルが生成されるため、実行時にそれらを読み取ることができない可能性があります。 これらを実行時に読み取るには、[こちら](#injecting-data-from-the-server-into-the-page)で説明するように、サーバー上のメモリに HTML を読み込み、実行時にプレースホルダーを置き換える必要があります。 また、これらを変更するたびに、サーバー上でアプリをリビルドすることもできます。

>注: 作成するカスタム環境変数は、`REACT_APP_` で始まる必要があります。 `NODE_ENV` を除く他の変数は、[同じ名前を持つ可能性のある秘密キーが誤ってコンピューター上で公開される](https://github.com/facebookincubator/create-react-app/issues/865#issuecomment-252199527)のを避けるために無視されます。 環境変数を変更した場合、開発サーバーが実行されていれば、再起動する必要があります。

これらの環境変数は、`process.env` で定義されます。 たとえば、`REACT_APP_SECRET_CODE` という名前の環境変数を使用すると、JS では `process.env.REACT_APP_SECRET_CODE` として公開されます。

さらに、`NODE_ENV` という名前の組み込み環境変数もあります。 これは、`process.env.NODE_ENV` から読み取ることができます。 これは、`npm start` を実行すると常に `'development'` と等しくなり、`npm test` を実行すると常に `'test'`と等しくなり、`npm run build` を実行して運用バンドルを作成すると、常に `'production'`と等しくなります。 **`NODE_ENV` を手動でオーバーライドすることはできません。** これにより、開発者が誤って、低速の開発ビルドを運用環境にデプロイするのを防ぐことができます。

これらの環境変数は、プロジェクトがデプロイされている場所に基づいて条件付きで情報を表示したり、バージョン管理の範囲外にある機密データを使用したりする場合に役立ちます。

最初に、環境変数を定義する必要があります。 たとえば、`<form>` 内の環境で定義されたシークレットを使用したいとします。

```jsx
render() {
  return (
    <div>
      <small>You are running this application in <b>{process.env.NODE_ENV}</b> mode.</small>
      <form>
        <input type="hidden" defaultValue={process.env.REACT_APP_SECRET_CODE} />
      </form>
    </div>
  );
}
```

ビルド時に、`process.env.REACT_APP_SECRET_CODE` は、`REACT_APP_SECRET_CODE` 環境変数の現在の値に置き換えられます。 `NODE_ENV` 変数は自動的に設定されることに注意してください。

ブラウザーにアプリを読み込んで、`<input>` を調べると、その値が `abcdef` に設定されていることがわかります。太字のテキストは、`npm start` を使用したときに提供される環境を示します。

```html
<div>
  <small>You are running this application in <b>development</b> mode.</small>
  <form>
    <input type="hidden" value="abcdef" />
  </form>
</div>
```

上記の形式は、環境から `REACT_APP_SECRET_CODE` という変数を探しています。 この値を使用するには、それが環境内で定義されている必要があります。 これは、シェルまたは `.env` ファイルのいずれかの方法を使用して行うことができます。 これらの両方の方法については、以降のいくつかのセクションで説明します。

`NODE_ENV` にアクセスできると、条件付きでアクションを実行する場合にも役立ちます。

```js
if (process.env.NODE_ENV !== 'production') {
  analytics.disable();
}
```

`npm run build` を使用してアプリをコンパイルすると、ミニファイ ステップによってこの条件が取り除かれ、結果として生成されるバンドルは縮小されます。

### <a name="referencing-environment-variables-in-the-html"></a>HTML での環境変数の参照

>注: この機能は、`react-scripts@0.9.0` 以降で使用できます。

`public/index.html` 内の `REACT_APP_` で始まる環境変数にアクセスすることもできます。 次に例を示します。

```html
<title>%REACT_APP_WEBSITE_NAME%</title>
```

上記のセクションの注意事項が適用されることに注意してください。

* 一部の組み込み変数 (`NODE_ENV` および `PUBLIC_URL`) を除いて、有効な変数名は `REACT_APP_` で始まる必要があります。
* 環境変数は、ビルド時に挿入されます。 実行時に挿入する必要がある場合、[代わりに次の方法に従います](#generating-dynamic-meta-tags-on-the-server)。

### <a name="adding-temporary-environment-variables-in-your-shell"></a>ご利用のシェルへの一時環境変数の追加

環境変数の定義は、OS によって異なる可能性があります。 この方法は、シェル セッションの有効期間中の一時的なものであることを知っておくことも重要です。

#### <a name="windows-cmdexe"></a>Windows (cmd.exe)

```cmd
set "REACT_APP_SECRET_CODE=abcdef" && npm start
```

(注:末尾の空白を避けるために、変数の割り当てを引用符で囲む必要があります。)

#### <a name="windows-powershell"></a>Windows (Powershell)

```Powershell
($env:REACT_APP_SECRET_CODE = "abcdef") -and (npm start)
```

#### <a name="linux-macos-bash"></a>Linux、macOS (Bash)

```bash
REACT_APP_SECRET_CODE=abcdef npm start
```

### <a name="adding-development-environment-variables-in-env"></a>`.env` への開発環境変数の追加

>注: この機能は、`react-scripts@0.5.0` 以降で使用できます。

永続的な環境変数を定義するには、プロジェクトのルートに、`.env` という名前のファイルを作成します。

```
REACT_APP_SECRET_CODE=abcdef
```
>注: 作成するカスタム環境変数は、`REACT_APP_` で始まる必要があります。 `NODE_ENV` を除く他の変数は、[同じ名前を持つ可能性のある秘密キーが誤ってコンピューター上で公開される](https://github.com/facebookincubator/create-react-app/issues/865#issuecomment-252199527)のを避けるために無視されます。 環境変数を変更した場合、開発サーバーが実行されていれば、再起動する必要があります。

`.env` ファイルをソース管理にチェックインする **必要があります**(`.env*.local`を除きます)。

#### <a name="what-other-env-files-are-can-be-used"></a>使用できるその他の `.env` ファイル

>注: この機能は、 **`react-scripts@1.0.0` 以降で使用できます**。

* `.env`: 既定値。
* `.env.local`: ローカル オーバーライド。 **このファイルは、テストを除くすべての環境で読み込まれます。**
* `.env.development`、`.env.test`、`.env.production`:環境固有の設定。
* `.env.development.local`、`.env.test.local`、`.env.production.local`:環境固有の設定のローカル オーバーライド。

左側のファイルの方が、右側のファイルよりも優先度が高くなります。

* `npm start`: `.env.development.local`, `.env.development`, `.env.local`, `.env`
* `npm run build`: `.env.production.local`, `.env.production`, `.env.local`, `.env`
* `npm test`: `.env.test.local`、`.env.test`、`.env` (`.env.local` がないことに注意してください)

マシンで明示的に設定されていない場合、これらの変数は既定値として使用されます。<br>
詳細については、[dotenv のドキュメント](https://github.com/motdotla/dotenv)を参照してください。

>注: 開発用の環境変数を定義している場合、CI やホスティング プラットフォームでもこれらを定義することが必要になる可能性があります。 この方法については、それぞれのドキュメントを参照してください。 たとえば、[Travis CI](https://docs.travis-ci.com/user/environment-variables/) または [Heroku](https://devcenter.heroku.com/articles/config-vars) のドキュメントを参照してください。

#### <a name="expanding-environment-variables-in-env"></a>`.env` 内の環境変数の展開

>注: この機能は、`react-scripts@1.1.0` 以降で使用できます。

`.env` ファイルで使用するためにマシン上に既にある変数を展開します ([dotenv-expand](https://github.com/motdotla/dotenv-expand) を使用)。

たとえば、環境変数 `npm_package_version` を取得するには、次のようにします。

```
REACT_APP_VERSION=$npm_package_version
# also works:
# REACT_APP_VERSION=${npm_package_version}
```

または、現在の `.env` ファイルに対してローカルな変数を展開します。

```
DOMAIN=www.example.com
REACT_APP_FOO=$DOMAIN/foo
REACT_APP_BAR=$DOMAIN/bar
```

## <a name="can-i-use-decorators"></a>デコレーターの使用

多くの一般的なライブラリでは、そのドキュメントで[デコレーター](https://medium.com/google-developers/exploring-es7-decorators-76ecb65fb841) が使用されています。<br>
Create React App では、現時点で、デコレーター構文はサポートされていません。理由は次のとおりです。

* これは試験的なプロポーザルであり、変更される可能性があります。
* 現在の仕様バージョンは、Bable で公式にサポートされていません。
* Facebook で内部的に使用されないため、仕様が変更されても codemod を作成できません。

ただし、多くの場合、デコレーターなしでデコレーターベースのコードを同じように書き直すことができます。<br>
参考のために、次の 2 つのスレッドを参照してください。

* [#214](https://github.com/facebookincubator/create-react-app/issues/214)
* [#411](https://github.com/facebookincubator/create-react-app/issues/411)

Create React App では、仕様が安定した段階に進んだときにデコレーターのサポートを追加します。

## <a name="fetching-data-with-ajax-requests"></a>AJAX 要求を使用したデータのフェッチ

React ではデータ フェッチへの特定のアプローチについて規定していませんが、通常、[axios](https://github.com/axios/axios)などのライブラリまたはブラウザーによって提供される[`fetch()`API](https://developer.mozilla.org/docs/Web/API/Fetch_API) のいずれかが使用されます。 便宜上、Create React App には、`fetch()` のポリフィルが含まれているため、ブラウザーのサポートについて心配することなく使用できます。

グローバル `fetch` 関数を使用すると、AJAX 要求を簡単に行うことができます。 これは、入力として URL を受け取り、`Response` オブジェクトに解決される `Promise` を返します。 `fetch` の詳細については、[こちら](https://developer.mozilla.org/docs/Web/API/Fetch_API/Using_Fetch)を参照してください。

このプロジェクトには、Promises/A+ の完全な実装を提供する [Promise polyfill](https://github.com/then/promise) も含まれます。 Promise は、非同期操作の最終的な結果を表します。Promise の詳細については、[こちら](https://www.promisejs.org/)および[こちら](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise)を参照してください。 axios と `fetch()` の両方で、Promise が内部的に使用されています。 [`async / await`](https://davidwalsh.name/async-await) 構文を使用して、コールバックの入れ子を減らすることもできます。

React コンポーネントから AJAX 要求を行う方法の詳細については、[React の Web サイトの FAQ エントリ](https://reactjs.org/docs/faq-ajax.html)を参照してください。

## <a name="integrating-with-an-api-backend"></a>API バックエンドとの統合

これらのチュートリアルは、アプリを別のポートで実行されている API バックエンドと統合し、`fetch()` を使用してそれにアクセスするのに役立ちます。

### <a name="node"></a>Node
[このチュートリアル](https://www.fullstackreact.com/articles/using-create-react-app-with-a-server/)を確認してください。
関連する GitHub リポジトリは[こちら](https://github.com/fullstackreact/food-lookup-demo)にあります。

### <a name="ruby-on-rails"></a>Ruby on Rails

[このチュートリアル](https://www.fullstackreact.com/articles/how-to-get-create-react-app-to-work-with-your-rails-api/)を確認してください。
関連する GitHub リポジトリは[こちら](https://github.com/fullstackreact/food-lookup-demo-rails)にあります。

## <a name="proxying-api-requests-in-development"></a>開発時に API 要求をプロキシ経由にする

>注: この機能は、`react-scripts@0.2.3` 以降で使用できます。

バックエンドの実装と同じホストとポートから、フロントエンドの React アプリを提供することがよくあります。<br>
たとえば、アプリをデプロイした後の運用環境のセットアップは、次のようになる場合があります。

```
/             - static server returns index.html with React app
/todos        - static server returns index.html with React app
/api/todos    - server handles any /api/* requests using the backend implementation
```

このようなセットアップは必須では **ありません**。 ただし、このようなセットアップが **ある** 場合は、開発中に別のホストまたはポートにリダイレクトすることを心配せず、`fetch('/api/todos')` のような要求を記述すると便利です。

すべての不明な要求を開発環境の API サーバーにプロキシするよう開発サーバーに指示するには、`proxy` フィールドを `package.json` に追加します。次に例を示します。

```js
  "proxy": "http://localhost:4000",
```

これにより、開発環境で `fetch('/api/todos')` を行うと、それが静的な資産ではないことが開発サーバーによって認識され、要求はフォールバックとして `http://localhost:4000/api/todos` にプロキシされます。 開発サーバーは、`text/html` Accept ヘッダーのない要求をプロキシに送信しようとするだけです。

好都合なことに、これにより開発環境での [CORS の問題](http://stackoverflow.com/questions/21854516/understanding-ajax-cors-and-security-considerations)と次のようなエラー メッセージが回避されます。

```
Fetch API cannot load http://localhost:4000/api/todos. No 'Access-Control-Allow-Origin' header is present on the requested resource. Origin 'http://localhost:3000' is therefore not allowed access. If an opaque response serves your needs, set the request's mode to 'no-cors' to fetch the resource with CORS disabled.
```

`proxy` は (`npm start` を使用する) 開発環境においてのみ効果があり、`/api/todos` のような URL が運用環境で適切なものを指し示すようにするのはユーザーの責任であることに注意してください。 `/api` プレフィックスを使用する必要はありません。 `text/html` Accept ヘッダーのない認識できない要求は、指定されている `proxy` にリダイレクトされます。

`proxy` オプションは、HTTP、HTTPS、WebSocket の各接続をサポートします。<br>
`proxy` オプションの柔軟性が十分では **ない** 場合は、次の方法があります。

* [プロキシを自分で構成する](#configuring-the-proxy-manually)
* サーバーで CORS を有効にします ([Express でそれを行う方法については、こちらを参照してください](http://enable-cors.org/server_expressjs.html))。
* [環境変数](#adding-custom-environment-variables)を使用して、適切なサーバー ホストとポートをアプリに挿入します。

### <a name="invalid-host-header-errors-after-configuring-proxy"></a>プロキシを構成した後の "無効なホスト ヘッダー" エラー

`proxy` オプションを有効にすると、より厳密な一連のホスト チェックが行われるようになります。 これは、バックエンドをリモート ホストに開いたままにすると、コンピューターが DNS 再バインド攻撃に対して脆弱になるので必要です。 この問題については、[こちらの記事](https://medium.com/webpack/webpack-dev-server-middleware-security-issues-1489d950874a)と[こちらのイシュー](https://github.com/webpack/webpack-dev-server/issues/887)で説明されています。

`localhost` で開発するときはこれによる影響はないはずですが、[こちらで説明されている](https://github.com/facebookincubator/create-react-app/issues/2271)ようにリモート環境で開発する場合は、`proxy` オプションを有効にした後、ブラウザーにこのエラーが表示されます。

>無効なホスト ヘッダー

この問題を回避するには、プロジェクトのルートにある `.env.development` という名前のファイルで、パブリック開発ホストを指定します。

```
HOST=mypublicdevhost.com
```

それから開発サーバーを再起動し、指定したホストからアプリを読み込むと、動作するようになるはずです。

まだ問題が発生する場合、またはクラウド エディターのようなさらに異質の環境を使用している場合は、`.env.development.local` に行を追加することで、ホスト チェックを完全にバイパスできます。 **これは危険であり、悪意のある Web サイトからのリモート コード実行にマシンがさらされることに注意してください。**

```
# NOTE: THIS IS DANGEROUS!
# It exposes your machine to attacks from the websites you visit.
DANGEROUSLY_DISABLE_HOST_CHECK=true
```

この方法はお勧めしません。

### <a name="configuring-the-proxy-manually"></a>プロキシの手動構成

>注: この機能は、`react-scripts@1.0.0` 以降で使用できます。

`proxy` オプションの柔軟性が十分では **ない** 場合は、次の形式でオブジェクトを (`package.json` で) 指定できます。<br>
また、構成値 [`http-proxy-middleware`](https://github.com/chimurai/http-proxy-middleware#options) または [`http-proxy`](https://github.com/nodejitsu/node-http-proxy#options) のサポートを指定することもできます。
```js
{
  // ...
  "proxy": {
    "/api": {
      "target": "<url>",
      "ws": true
      // ...
    }
  }
  // ...
}
```

このパスに一致するすべての要求はプロキシであり、例外にはなりません。 これには `text/html` に対する要求が含まれ、標準の `proxy` オプションではプロキシされません。

複数のプロキシを指定する必要がある場合は、追加のエントリを指定することにより行うことができます。
また、`*` および `**` を使用して厳密なパスまたは任意のサブパスと一致させることで、一致を絞り込むこともできます。
```js
{
  // ...
  "proxy": {
    // Matches any request starting with /api
    "/api": {
      "target": "<url_1>",
      "ws": true
      // ...
    },
    // Matches any request starting with /foo
    "/foo": {
      "target": "<url_2>",
      "ssl": true,
      "pathRewrite": {
        "^/foo": "/foo/beta"
      }
      // ...
    },
    // Matches /bar/abc.html but not /bar/sub/def.html
    "/bar/*.html": {
      "target": "<url_3>",
      // ...
    },
    // Matches /baz/abc.html and /baz/sub/def.html
    "/baz/**/*.html": {
      "target": "<url_4>"
      // ...
    }
  }
  // ...
}
```

### <a name="configuring-a-websocket-proxy"></a>WebSocket プロキシの構成

WebSocket プロキシを設定する場合は、さらにいくつかの考慮事項に注意する必要があります。

[Socket.io](https://socket.io/) などの WebSocket エンジンを使用する場合は、プロキシ ターゲットとして使用できる Socket.io サーバーを実行している必要があります。 Socket.io は、標準の WebSocket サーバーでは動作しません。 具体的には、Socket.io は [websocket.org エコー テスト](http://websocket.org/echo.html)で機能すると思わないでください。

[Socket.io サーバーのセットアップ](https://socket.io/docs/)に関するよいドキュメントがいくつかあります。

標準の WebSocket は、標準の WebSocket サーバーと websocket.org エコー テストで **動作します**。 [ブラウザーのネイティブ WebSocket](https://developer.mozilla.org/docs/Web/API/WebSocket) では、サーバー用の [ws](https://github.com/websockets/ws) のようなライブラリを使用できます。

どちらの方法でも、`package.json` で WebSocket 要求を手動でプロキシできます。

```js
{
  // ...
  "proxy": {
    "/socket": {
      // Your compatible WebSocket server
      "target": "ws://<socket_url>",
      // Tell http-proxy-middleware that this is a WebSocket proxy.
      // Also allows you to proxy WebSocket requests without an additional HTTP request
      // https://github.com/chimurai/http-proxy-middleware#external-websocket-upgrade
      "ws": true
      // ...
    }
  }
  // ...
}
```

## <a name="using-https-in-development"></a>開発での HTTPS の使用

>注: この機能は、`react-scripts@0.4.0` 以降で使用できます。

HTTPS 経由でページを提供するには、開発サーバーが必要な場合があります。 これが役に立つ可能性がある具体的なケースの 1 つは、API サーバー自体が HTTPS を提供している場合に、["プロキシ" 機能](#proxying-api-requests-in-development)を使用して API サーバーに要求をプロキシする場合です。

これを行うには、`HTTPS` 環境変数を `true` に設定してから、通常どおり `npm start` で開発サーバーを起動します。

#### <a name="windows-cmdexe"></a>Windows (cmd.exe)

```cmd
set HTTPS=true&&npm start
```

#### <a name="windows-powershell"></a>Windows (Powershell)

```Powershell
($env:HTTPS = $true) -and (npm start)
```

(注: 空白がないのは意図的なものです。)

#### <a name="linux-macos-bash"></a>Linux、macOS (Bash)

```bash
HTTPS=true npm start
```

サーバーでは自己署名証明書が使用されるため、Web ブラウザーでページにアクセスすると、ほぼ間違いなく警告が表示されることに注意してください。

## <a name="generating-dynamic-meta-tags-on-the-server"></a>サーバーでの動的 `<meta>` タグの生成

Create React App ではサーバー レンダリングがサポートされていないため、`<meta>` タグを動的にして現在の URL を反映する方法がわからないかもしれません。 これを解決するには、次のように HTML にプレースホルダーを追加することをお勧めします。

```html
<!doctype html>
<html lang="en">
  <head>
    <meta property="og:title" content="__OG_TITLE__">
    <meta property="og:description" content="__OG_DESCRIPTION__">
```

その後は、使用するバックエンドに関係なく、サーバーで、`index.html` をメモリに読み取り、`__OG_TITLE__`、`__OG_DESCRIPTION__`、および他のプレースホルダーを、現在の URL に依存する値に置き換えることができます。 補間された値を HTML に埋め込んでも安全なように、そのサニタイズとエスケープを行うことだけを注意してください。

Node サーバーを使用する場合は、クライアントとサーバーの間でルート一致ロジックを共有することもできます。 ただし、単純な場合はそれを複製しても問題なく動作します。

## <a name="pre-rendering-into-static-html-files"></a>静的 HTML ファイルへのプリレンダリング

静的ホスティング プロバイダーで `build` をホストしている場合は、[react-snapshot](https://www.npmjs.com/package/react-snapshot) を使用して、アプリケーション内の各ルートまたは相対リンクへの HTML ページを生成できます。 これらのページは、JavaScript バンドルが読み込まれると、シームレスにアクティブになります ("ハイドレート" されます)。

また、静的ホスティングの外部でこれを使用して、ルートの生成とキャッシュを行うときのサーバーの負荷を取り除くこともでき。

プリレンダリングの主な利点は、JavaScript のバンドルが正常にダウンロードされたかどうかに関係なく、HTML のペイロードを "使用して" 各ページのコア コンテンツを取得できることです。 また、アプリケーションの各ルートが検索エンジンによって取得される可能性も高くなります。

[こちらでゼロ構成のプリレンダリング (スナップショット作成とも呼ばれます)](https://medium.com/superhighfives/an-almost-static-stack-6df0a2791319) の詳細を参照してください。

## <a name="injecting-data-from-the-server-into-the-page"></a>サーバーからページへのデータの挿入

前のセクションと同様に、グローバル変数を挿入する一部のプレースホルダーを HTML に残しておくことができます。次に例を示します。

```js
<!doctype html>
<html lang="en">
  <head>
    <script>
      window.SERVER_DATA = __SERVER_DATA__;
    </script>
```

その後、サーバー上で、応答を送信する直前に、`__SERVER_DATA__` を実際のデータの JSON に置き換えることができます。 `window.SERVER_DATA` をクライアント コードを読み取って使用できます。 **アプリが XSS 攻撃に対して脆弱になるので、[クライアントに送信する前に JSON をサニタイズ](https://medium.com/node-security/the-most-common-xss-vulnerability-in-react-js-applications-2bdffbcc1fa0)してください。**

## <a name="running-tests"></a>テストの実行

>注: この機能は、`react-scripts@0.3.0` 以降で使用できます。<br>
>[古いプロジェクトで有効にする方法については、移行ガイドを参照してください。](https://github.com/facebookincubator/create-react-app/blob/master/CHANGELOG.md#migrating-from-023-to-030)

Create React App は、テスト ランナーとして [Jest](https://facebook.github.io/jest/) を使用します。 この統合を準備するため、Jest を[大幅に改良](https://facebook.github.io/jest/blog/2016/09/01/jest-15.html)したので、以前に悪い評判を聞いたことがある場合は、もう一度試してみてください。

Jest は Node ベースのランナーです。 つまり、テストは、実際のブラウザーではなく、Node 環境で常に実行されます。 これにより、繰り返しがいっそう高速化され、断片化を防ぐことができます。

Jest は [jsdom](https://github.com/tmpvar/jsdom) を利用して `window` などのブラウザー グローバルを提供しますが、実際のブラウザーの動作の近似でしかありません。 Jest は、DOM の異常ではなく、ロジックとコンポーネントの単体テストに使用することが意図されています。

ブラウザーのエンドツーエンドのテストが必要な場合は、別のツールを使用することをお勧めします。 これらは、Create React App の範囲外です。

### <a name="filename-conventions"></a>ファイル名の規則

Jest では、次の一般的な名前付け規則のいずれかを使用してテスト ファイルを探します。

* `__tests__` フォルダー内の `.js` サフィックスが付くファイル。
* `.test.js` サフィックスが付くファイル。
* `.spec.js` サフィックスが付くファイル。

`.test.js` / `.spec.js` ファイル (または `__tests__` フォルダー) は、任意の深さの最上位の `src` フォルダーの下にあります。

相対インポートがより短く見えるように、テストするコードの横にテスト ファイル (または `__tests__` フォルダー) を置くことをお勧めします。 たとえば、`App.test.js` と `App.js` が同じフォルダー内にある場合、長い相対パスではなく、`import App from './App'` に対するテストのみで済みます。 コロケーションも、大規模なプロジェクトでテストをよりすばやく見つけるのに役立ちます。

### <a name="command-line-interface"></a>コマンド ライン インターフェイス

`npm test` を実行すると、Jest がウォッチ モードで起動します。 ファイルを保存するたびに、`npm start` でコードを再コンパイルするのと同じように、テストが再実行されます。

ウォッチャーには、すべてのテストを実行したり、検索パターンに焦点を当てたりする機能を備えた対話型のコマンド ライン インターフェイスが含まれています。 開いたまま、すばやく再実行できるように設計されています。 コマンドについては、毎回実行後にウォッチャーに出力される [Watch Usage] メモを参照してください。

![Jest ウォッチ モード](http://facebook.github.io/jest/img/blog/15-watch.gif)

### <a name="version-control-integration"></a>バージョン管理の統合

既定では、`npm test` を実行すると、Jest により、前回のコミット以降に変更されたファイルに関連するテストのみが実行されます。 これは、テストの数に関係なく、テストを高速で実行するように設計された最適化です。 ただし、テストに合格しないコードを頻繁にコミットしないことを前提とします。

Jest では常に、前回のコミット以降に変更されたファイルに関連するテストのみを実行したことが明示的に示されます。 ウォッチ モードで `a` キーを押して、Jest に強制的にすべてのテストを実行させることもできます。

Jest では常に、[継続的インテグレーション](#continuous-integration) サーバー上で、あるいはプロジェクトが Git や Mercurial リポジトリ内に含まれていない場合はすべてのテストを実行します。

### <a name="writing-tests"></a>テストの作成

テストを作成するには、テストの名前とそのコードを含む `it()` (または `test()`) ブロックを追加します。 必要に応じて、論理的なグループ化のためにそれらを `describe()` ブロックにラップできますが、これは必須ではなく、推奨されることでもありません。

Jest では、アサーションを行うための組み込みの `expect()` グローバル関数が提供されます。 基本的なテストはこのようになります。

```js
import sum from './sum';

it('sums numbers', () => {
  expect(sum(1, 2)).toEqual(3);
  expect(sum(2, 2)).toEqual(4);
});
```

Jest でサポートされているすべての `expect()` マッチャーは、[こちらに広範に記載](http://facebook.github.io/jest/docs/expect.html)されています。<br>
また、[`jest.fn()` と `expect(fn).toBeCalled()`](http://facebook.github.io/jest/docs/expect.html#tohavebeencalled) を使用して、"スパイ" またはモック関数を作成できます。

### <a name="testing-components"></a>コンポーネントのテスト

コンポーネント テストには広範な手法があります。 コンポーネントがスローせずにレンダリングされるのを確認する "スモーク テスト" から、一部の出力の浅いレンダリングとテスト、コンポーネントのライフサイクルと状態変更の完全なレンダリングとテストまで、さまざまなものがあります。

異なるプロジェクトでは、コンポーネントが変更される頻度と、それらに含まれるロジックの量に基づいて、異なるテストのトレードオフが選択されます。 テスト戦略をまだ決定していない場合は、まずコンポーネントに対してシンプルなスモーク テストを作成することをお勧めします。

```ts
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import App from './App';

it('renders without crashing', () => {
  const div = document.createElement('div');
  ReactDOM.render(<App />, div);
});
```

このテストではコンポーネントをマウントし、レンダリング中にスローしなかったことを確認します。 このようなテストでは、非常に少ない労力で多くの価値が提供されるため、開始点として最適です。これは、`src/App.test.tsx` に含まれるテストです。

コンポーネントの変更によってバグが発生した場合、アプリケーションでテストする価値のある部分に関するより深い分析情報が得られます。 これは、特定の予想される出力または動作をアサートするより具体的なテストを導入する場合に便利な場合があります。

レンダリングする子コンポーネントとは別にコンポーネントをテストしたい場合は、[Enzyme](http://airbnb.io/enzyme/) の [`shallow()` レンダリング API](http://airbnb.io/enzyme/docs/api/shallow.html) を使用することをお勧めします。 このプラグインをインストールするには、次のコードを実行します。

```sh
npm install --save-dev enzyme @types/enzyme enzyme-adapter-react-16 @types/enzyme-adapter-react-16 react-test-renderer @types/react-test-renderer
```

または、`yarn` を使用することもできます。

```sh
yarn add --dev enzyme @types/enzyme enzyme-adapter-react-16 @types/enzyme-adapter-react-16 react-test-renderer @types/react-test-renderer
```

#### `src/setupTests.ts`
```ts
import * as Enzyme from 'enzyme';
import * as Adapter from 'enzyme-adapter-react-16';

Enzyme.configure({ adapter: new Adapter() });
```

>注: `src/setupTests.js` を作成する前に "取り出す" ことにした場合は、結果の `package.json` ファイルにそれへの参照が含まれないことに注意してください。 取り出し後にこれを追加する方法については、[こちらを参照](#initializing-test-environment)してください。

これで、スモーク テストを記述できるようになりました。

```ts
import * as React from 'react';
import { shallow } from 'enzyme';
import App from './App';

it('renders without crashing', () => {
  shallow(<App />);
});
```

`ReactDOM.render()` を使用した以前のスモーク テストとは異なり、このテストでは `<App>` のレンダリングのみを行い、掘り下げません。 たとえば、`<App>` 自体で、スローする `<Button>` をレンダリングした場合でも、このテストは合格します。 浅いレンダリングは、分離された単体テストには最適ですが、コンポーネントが確実に正しく統合されるように引き続き完全なレンダリング テストをいくつか作成する必要がある場合があります。 Enzyme では [`mount()` を使用した完全なレンダリング](http://airbnb.io/enzyme/docs/api/mount.html)がサポートされており、状態の変更とコンポーネントのライフサイクルのテストにも使用できます。

その他のテスト手法については、[Enzyme ドキュメント](http://airbnb.io/enzyme/)を参照してください。 Enzyme ドキュメントではアサーションに Chai と Sinon が使用されますが、Jest ではスパイに組み込みの `expect()` と `jest.fn()` が提供されるため、それらを使用する必要はありません。

以下に示すのは、特定の出力をアサートする Enzyme ドキュメントからの例です。これは、Jest マッチャーを使用するために書き換えられています。

```ts
import * as React from 'react';
import { shallow } from 'enzyme';
import App from './App';

it('renders welcome message', () => {
  const wrapper = shallow(<App />);
  const welcome = <h2>Welcome to React</h2>;
  // expect(wrapper.contains(welcome)).to.equal(true);
  expect(wrapper.contains(welcome)).toEqual(true);
});
```

すべての Jest マッチャーは、[ここに広範に記載](http://facebook.github.io/jest/docs/expect.html)されています。<br>
それでも、以下の説明のとおり、必要に応じて [Chai](http://chaijs.com/) のようなサードパーティのアサーション ライブラリを使用できます。

また、読み取り可能なマッチャーでテストを簡略化するのに [jest-enzyme](https://github.com/blainekasten/enzyme-matchers) が役立つ場合があります。 上記の `contains` コードは、jest-enzyme を使用してより簡単に記述できます。

```js
expect(wrapper).toContainReact(welcome)
```

これを有効にするには、`jest-enzyme` をインストールします。

```sh
npm install --save jest-enzyme
```

`yarn` を使用することもできます。

```sh
yarn add jest-enzyme
```

それを [`src/setupTests.ts`](#initializing-test-environment) にインポートし、そのマッチャーをすべてのテストで使用できるようにします。

```js
import 'jest-enzyme';
```

### <a name="using-third-party-assertion-libraries"></a>サード パーティ アサーション ライブラリの使用

アサーションには `expect()` を使用し、スパイには `jest.fn()` を使用することをお勧めします。 問題が発生した場合は、[Jest に対して提出](https://github.com/facebook/jest/issues/new)してください。こちらで修正します。 [JSX としての React 要素の整形出力](https://github.com/facebook/jest/pull/1566)などをサポートする React 用に、引き続き改善を行う予定です。

ただし、[Chai](http://chaijs.com/) や [Sinon](http://sinonjs.org/) などの他のライブラリに慣れている場合、または移植するものを使用している既存のコードがある場合、通常はこのようにインポートできます。

```js
import sinon from 'sinon';
import { expect } from 'chai';
```

その後、通常どおりテストで使用できます。

### <a name="initializing-test-environment"></a>テスト環境の初期化

>注: この機能は、`react-scripts@0.4.0` 以降で使用できます。

テストでモックを作成する必要があるブラウザー API がアプリで使用されている場合、またはテストを実行する前にグローバル セットアップが必要なだけの場合は、`src/setupTests.ts` をプロジェクトに追加します。 これはテストを実行する前に自動的に行われます。

次に例を示します。

#### `src/setupTests.ts`
```ts
const localStorageMock = {
  getItem: jest.fn(),
  setItem: jest.fn(),
  clear: jest.fn()
};
global.localStorage = localStorageMock
```

>注: `src/setupTests.js` を作成する前に "取り出す" ことにした場合は、結果の `package.json` ファイルにそれへの参照が含まれなくなるため、Jest の構成でプロパティ `setupTestFrameworkScriptFile` を手動で作成する必要があることに注意してください。例を以下に示します。

>```js
>"jest": {
>   // ...
>   "setupTestFrameworkScriptFile": "<rootDir>/src/setupTests.js"
>  }
>  ```

### <a name="focusing-and-excluding-tests"></a>テストの絞り込みと除外

`it()` を `xit()` に置き換え、実行対象からテストを一時的に除外することができます。<br>
同様に、`fit()` を使用して、他のテストを実行せずに特定のテストに絞り込むことができます。

### <a name="coverage-reporting"></a>カバレッジ レポート

Jest には、ES6 で適切に機能し、構成を必要としない統合カバレッジ レポーターがあります。<br>
カバレッジ レポートを含めるには、このように `npm test -- --coverage` を実行します (中央の `--` に注意してください)。

![カバレッジ レポート](http://i.imgur.com/5bFhnTS.png)

カバレッジではテストの実行速度がかなり低下するため、通常のワークフローとは別に実行することをお勧めします。

### <a name="continuous-integration"></a>継続的インテグレーション

既定では、`npm test` で対話型 CLI を使用してウォッチャーが実行されます。 しかし、`CI` という環境変数を設定することで、テストを強制的に 1 回実行し、プロセスを完了することができます。

`npm run build` を使用してアプリケーションのビルドを作成する場合、既定ではリンター警告が確認されません。 `npm test` と同様に、環境変数 `CI` を設定することで、ビルドで強制的にリンター警告を確認することができます。 警告が示された場合、ビルドは失敗します。

一般的な CI サーバーでは既定で環境変数 `CI` が既に設定されていますが、これは自分で行うこともできます。

### <a name="on-ci-servers"></a>CI サーバー上の場合
#### <a name="travis-ci"></a>Travis CI

1. Travis と GitHub リポジトリを同期する場合は、[Travis のはじめに](https://docs.travis-ci.com/user/getting-started/)のガイドに従います。  [プロファイル](https://travis-ci.org/profile) ページで一部の設定を手動で初期化する必要がある場合があります。
1. Git リポジトリに `.travis.yml` ファイルを追加します。
```
language: node_js
node_js:
  - 6
cache:
  directories:
    - node_modules
script:
  - npm run build
  - npm test
```
1. git プッシュを使用して最初のビルドをトリガーします。
1. 必要に応じて、[Travis CI ビルドをカスタマイズ](https://docs.travis-ci.com/user/customizing-the-build/)します。

#### <a name="circleci"></a>CircleCI

[この記事](https://medium.com/@knowbody/circleci-and-zeits-now-sh-c9b7eebcd3c1)に従い、Create React App プロジェクトを使用して CircleCI を設定します。

### <a name="on-your-own-environment"></a>独自の環境の場合
##### <a name="windows-cmdexe"></a>Windows (cmd.exe)

```cmd
set CI=true&&npm test
```

```cmd
set CI=true&&npm run build
```

(注: 空白がないのは意図的なものです)。

##### <a name="windows-powershell"></a>Windows (Powershell)

```Powershell
($env:CI = $true) -and (npm test)
```

```Powershell
($env:CI = $true) -and (npm run build)
```

##### <a name="linux-macos-bash"></a>Linux、macOS (Bash)

```bash
CI=true npm test
```

```bash
CI=true npm run build
```

test コマンドを使用すると、ウォッチャーは起動されずに、強制的に Jest でテストが 1 回実行されます。

>  開発環境でこれが頻繁に発生する場合、Microsoft はウォッチャーを最適なエクスペリエンスにしたいと考え、より多くのワークフローに対応するように変更するので、[イシューに登録](https://github.com/facebookincubator/create-react-app/issues/new)してお客様のユース ケースをお知らせください。

build コマンドはリンターの警告をチェックし、見つかった場合は失敗します。

### <a name="disabling-jsdom"></a>jsdom の無効化

既定では、生成されるプロジェクトの `package.json` は次のようになります。

```js
  "scripts": {
    "start": "react-scripts start",
    "build": "react-scripts build",
    "test": "react-scripts test --env=jsdom"
```

どのテストも [jsdom](https://github.com/tmpvar/jsdom) に依存しないことがわかっている場合は、`--env=jsdom` を削除しても安全であり、テストの実行が速くなります。

```diff
  "scripts": {
    "start": "react-scripts start",
    "build": "react-scripts build",
-   "test": "react-scripts test --env=jsdom"
+   "test": "react-scripts test"
```

判断できるように、**jsdom を必要とする** API の一覧を次に示します。

* `window` や `document` のような任意のブラウザー グローバル
* [`ReactDOM.render()`](https://facebook.github.io/react/docs/top-level-api.html#reactdom.render)
* [`TestUtils.renderIntoDocument()`](https://facebook.github.io/react/docs/test-utils.html#renderintodocument) (上記に対する[ショートカット](https://github.com/facebook/react/blob/34761cf9a252964abfaab6faf74d473ad95d1f21/src/test/ReactTestUtils.js#L83-L91))
* [Enzyme](http://airbnb.io/enzyme/index.html) の [`mount()`](http://airbnb.io/enzyme/docs/api/mount.html)

一方、次の API には **jsdom は必要ありません**。

* [`TestUtils.createRenderer()`](https://facebook.github.io/react/docs/test-utils.html#shallow-rendering) (浅いレンダリング)
* [Enzyme](http://airbnb.io/enzyme/index.html) の [`shallow()`](http://airbnb.io/enzyme/docs/api/shallow.html)

最後に、jsdom は[スナップショット テスト](http://facebook.github.io/jest/blog/2016/07/27/jest-14.html)にも必要ありません。

### <a name="snapshot-testing"></a>スナップショット テスト

スナップショット テストは Jest の機能であり、コンポーネントのテキスト スナップショットが自動的に生成されて、ディスクに保存されるので、UI 出力が変更された場合は、コンポーネント出力にアサーションを手動で書き込まなくても通知を受け取ります。 [スナップショット テストの詳細を参照してください。](http://facebook.github.io/jest/blog/2016/07/27/jest-14.html)

### <a name="editor-integration"></a>エディターとの統合

[Visual Studio Code](https://code.visualstudio.com) を使用している場合は、[Jest 拡張機能](https://github.com/orta/vscode-jest)があり、何もしなくても Create React App で動作します。 これにより、テスト実行の状態と可能性のあるエラー メッセージのインラインでの表示、ウォッチャーの自動的な開始と停止、ワンクリック スナップショット更新の提供など、IDE に似た多くの機能がテキスト エディターの使用中に提供されます。

![VS Code Jest のプレビュー](https://cloud.githubusercontent.com/assets/49038/20795349/a032308a-b7c8-11e6-9b34-7eeac781003f.png)

## <a name="debugging-tests"></a>テストのデバッグ

Jest テスト用にデバッガーを設定するには、さまざまな方法があります。 Chrome と [Visual Studio Code](https://code.visualstudio.com/) でのデバッグについて説明します。

>注: テストのデバッグには、Node 8 以降が必要です。

### <a name="debugging-tests-in-chrome"></a>Chrome でのテストのデバッグ

プロジェクトの `package.json` の `scripts` セクションに、以下を追加します
```json
"scripts": {
    "test:debug": "react-scripts --inspect-brk test --runInBand --env=jsdom"
  }
```
`debugger;` ステートメントを任意のテストに配置して実行します。
```bash
$ npm run test:debug
```

これにより Jest テストの実行が開始されますが、デバッガーがプロセスにアタッチできるよう、実行前に一時停止します。

Chrome で以下を開きます
```
about:inspect
```

そのリンクを開くと、Chrome のデベロッパー ツール表示されます。 プロセスで `inspect` を選択すると、React スクリプトの最初の行にブレークポイントが設定されます (これは単に、Jest が実行される前に、デベロッパー ツールを開くことができるようにするためだけに行われます)。 画面の右上にある "再生" ボタンのようなボタンをクリックして、実行を続けます。 Jest によってデバッガー ステートメントが含まれるテストが実行されると、実行は一時停止し、現在のスコープと呼び出し履歴を確認できます。

>注: --runInBand cli オプションを使用すると、Jest は、個々のテスト用にプロセスを生成するのではなく、同じプロセスでテストを実行します。 通常、テストの実行は Jest によってプロセス間に並列化されますが、多くのプロセスを同時にデバッグするのは困難です。

### <a name="debugging-tests-in-visual-studio-code"></a>Visual Studio Code でのテストのデバッグ

[Visual Studio Code](https://code.visualstudio.com) では、Jest テストのデバッグが既定でサポートされています。

次の [`launch.json`](https://code.visualstudio.com/docs/editor/debugging#_launch-configurations) 構成ファイルを使用します。
```
{
  "version": "0.2.0",
  "configurations": [
    {
      "name": "Debug CRA Tests",
      "type": "node",
      "request": "launch",
      "runtimeExecutable": "${workspaceRoot}/node_modules/.bin/react-scripts",      
      "args": [
        "test",
        "--runInBand",
        "--no-cache",
        "--env=jsdom"
      ],
      "cwd": "${workspaceRoot}",
      "protocol": "inspector",
      "console": "integratedTerminal",
      "internalConsoleOptions": "neverOpen"
    }
  ]
}
```

## <a name="developing-components-in-isolation"></a>コンポーネントを分離して開発

通常、アプリには多数の UI コンポーネントがあり、それぞれに多くの異なる状態があります。
たとえば、単純なボタン コンポーネントの状態は次のようになります。

* テキスト ラベルの付いた通常の状態。
* 無効モード。
* 読み込み中状態。

通常、サンプル アプリや例を実行しないと、これらの状態を確認するのは難しい場合があります。

Create React App には既定ではこのためのツールは含まれませんが、[Storybook for React](https://storybook.js.org) ([ソース](https://github.com/storybooks/storybook)) または [React Styleguidist](https://react-styleguidist.js.org/) ([ソース](https://github.com/styleguidist/react-styleguidist)) をプロジェクトに簡単に追加できます。 **これらは、コンポーネントを開発し、アプリから切り離してすべての状態を確認できる、サードパーティ製のツールです**。

![Storybook for React のデモ](http://i.imgur.com/7CIAWpB.gif)

Storybook またはスタイル ガイドを静的アプリとしてデプロイすることもできます。 このようにすると、チームの全員が、バックエンド サーバーを起動したり、アプリでアカウントを作成したりすることなく、UI コンポーネントのさまざまな状態を表示して確認できます。

### <a name="getting-started-with-storybook"></a>Storybook の概要

Storybook は、React UI コンポーネント用の開発環境です。 それを使用すると、コンポーネント ライブラリを参照し、各コンポーネントのさまざまな状態を表示し、コンポーネントを対話形式で開発およびテストすることができます。

最初に、次の npm パッケージをグローバルにインストールします。

```sh
npm install -g @storybook/cli
```

次に、アプリのディレクトリ内で下記のコマンドを実行します。

```sh
getstorybook
```

その後は、画面の手順に従います。

React Storybook の詳細を確認してください。

* スクリーンキャスト:[React Storybook の概要](https://egghead.io/lessons/react-getting-started-with-react-storybook)
* [GitHub リポジトリ](https://github.com/storybooks/storybook)
* [ドキュメント](https://storybook.js.org/basics/introduction/)
* [スナップショット テスト UI](https://github.com/storybooks/storybook/tree/master/addons/storyshots) と Storybook + アドオン/ストーリーショット

### <a name="getting-started-with-styleguidist"></a>Styleguidist の概要

Styleguidist は、すべてのコンポーネントとそれらの props ドキュメントおよび使用例が 1 つのページに表示されるスタイル ガイドと、Storybook と同様にコンポーネントを分離して開発するための環境が、組み合わされたものです。 Styleguidist では、Markdown で例を記述し、各コード スニペットはライブ編集可能なプレイグラウンドとしてレンダリングされます。

最初に、Styleguidist をインストールします。

```sh
npm install --save react-styleguidist
```

または、`yarn` を使用することもできます。

```sh
yarn add react-styleguidist
```

次に、これらのスクリプトを `package.json` に追加します。

```diff
   "scripts": {
+    "styleguide": "styleguidist server",
+    "styleguide:build": "styleguidist build",
     "start": "react-scripts start",
```

次に、アプリのディレクトリ内で下記のコマンドを実行します。

```sh
npm run styleguide
```

その後は、画面の手順に従います。

React Styleguidist の詳細を参照してください。

* [GitHub リポジトリ](https://github.com/styleguidist/react-styleguidist)
* [ドキュメント](https://react-styleguidist.js.org/docs/getting-started.html)

## <a name="publishing-components-to-npm"></a>npm へのコンポーネントの発行

Create React App には、npm にコンポーネントを発行するための組み込み機能は用意されていません。 他のユーザーが使用できるよう、プロジェクトからコンポーネントを抽出する準備ができたら、自分のプロジェクトの外部にある別のディレクトリにそれを移動してから、[nwb](https://github.com/insin/nwb#react-components-and-libraries) などのツールを使用して発行用に準備することをお勧めします。

## <a name="making-a-progressive-web-app"></a>プログレッシブ Web アプリの作成

既定では、運用ビルドは完全に機能するオフラインファーストの[プログレッシブ Web アプリ](https://developers.google.com/web/progressive-web-apps/)です。

プログレッシブ Web アプリは、従来の Web ページより高速で信頼性が高く、魅力的なモバイル エクスペリエンスを提供します。

 * ネットワークの接続 (2G や 3G など) に関係なく、後続のアクセス時にページが速く読み込まれるよう、すべての静的サイト資産がキャッシュされます。 更新プログラムはバックグラウンドでダウンロードされます。
 * オフラインの場合でも、アプリはネットワークの状態に関係なく動作します。 つまり、ユーザーはアプリを 10,000 フィートの上空でも地下鉄でも使用できます。
 * モバイル デバイスでは、アプリをユーザーのホーム画面、アプリ アイコン、すべてのものに直接追加できます。 また、Web **プッシュ通知** を使用してユーザーの関心を再び引くこともできます。 これにより、アプリ ストアが不要になります。

運用構成に統合された [`sw-precache-webpack-plugin`](https://github.com/goldhand/sw-precache-webpack-plugin) によって、サービス ワーカー ファイルの生成が行われて、すべてのローカル資産が自動的に事前キャッシュされ、更新プログラムのデプロイに合わせて最新の状態に保たれます。
サービス ワーカーは、最初の HTML を含むローカル資産のすべての要求を処理するために[キャッシュファースト戦略](https://developers.google.com/web/fundamentals/instant-and-offline/offline-cookbook/#cache-falling-back-to-network)を使用し、低速または低信頼性のネットワーク上でも Web アプリは確実に高速で動作します。

### <a name="opting-out-of-caching"></a>キャッシュのオプトアウト

最初の運用デプロイの前にサービス ワーカーを有効にしたくない場合は、[`src/index.js`](src/index.js) から `serviceWorkerRegistration.register()` の呼び出しを削除します。

以前に運用デプロイでサービス ワーカーを有効にしてあり、既存のすべてのユーザーに対してそれを無効にすることを決定した場合は、[`src/index.js`](src/index.js) での `serviceWorkerRegistration.register()` の呼び出しを `serviceWorkerRegistration.unregister()` の呼び出しに置き換えることができます。
`serviceWorkerRegistration.unregister()` が含まれるページにユーザーがアクセスした後、サービス ワーカーはアンインストールされます。 `/service-worker.js` の提供方法によっては、キャッシュが無効になるのに最大で 24 時間かかる場合があることに注意してください。

### <a name="offline-first-considerations"></a>オフラインファーストの考慮事項

1. サービス ワーカーには [HTTPS が必要](https://developers.google.com/web/fundamentals/getting-started/primers/service-workers#you_need_https)ですが、ローカル テストを容易にするため、そのポリシーは [`localhost` には適用されません](http://stackoverflow.com/questions/34160509/options-for-testing-service-workers-via-http/34161385#34161385)。
運用 Web サーバーで HTTPS がサポートされていない場合、サービス ワーカーの登録は失敗しますが、Web アプリの残りの部分は機能します。

1. サービス ワーカーは、すべての Web ブラウザーで[現在はサポートされていません](https://jakearchibald.github.io/isserviceworkerready/)。 サポートのないブラウザーでは、サービス ワーカーの登録は[試みられません](src/registerServiceWorker.js)。

1. サービス ワーカーは、`npm run build` の出力など、[運用環境](#deployment)でのみ有効になります。 以前にキャッシュされた資産が使用され、ローカルで行った最新の変更が含まれない場合、不満を招く可能性があるので、開発環境でオフラインファーストのサービス ワーカーを有効にしないことをお勧めします。

1. オフラインファースト サービスワーカーをローカルでテストする ''*必要がある*'' 場合は、(`npm run build` を使用して) アプリケーションをビルドし、ビルド ディレクトリからシンプルな http サーバーを実行します。 ビルド スクリプトを実行した後、`create-react-app` によって、運用ビルドをローカルでテストするための手順が提供されます。その[デプロイ手順](#deployment)には、他のメソッドを使用するための手順が含まれています。 *ブラウザー キャッシュに関する複雑さを回避するために、常に incognito ウィンドウを使用するようにしてください。*

1. 可能であれば、[HTTP キャッシュを無効にして](http://stackoverflow.com/questions/38843970/service-worker-javascript-update-frequency-every-24-hours)生成された `service-worker.js` を提供するように運用環境を構成します。
可能でない (たとえば、[GitHub ページ](#github-pages)で既定の 10 分の HTTP キャッシュ有効期間を変更できない) 場合は、運用サイトにアクセスし、HTTP キャッシュから `service-worker.js` の有効期限が切れる前にもう一度再アクセスすると、サービス ワーカーから以前にキャッシュされた資産を引き続き取得できることに注意してください。 更新された運用環境のデプロイをすぐに確認する必要がある場合は、Shift キーを押しながら更新を実行すると、サービス ワーカーが一時的に無効になり、ネットワークからすべての資産が取得されます。

1. ユーザーが必ずしもオフラインファーストの Web アプリに慣れているわけではありません。 サービス ワーカーでキャッシュの取り込みが完了したことを[ユーザーに知らせ](https://developers.google.com/web/fundamentals/instant-and-offline/offline-ux#inform_the_user_when_the_app_is_ready_for_offline_consumption) ("この Web アプリはオフラインで動作しています" というメッセージを示す)、また、次回のページの読み込み時に利用可能になる最新の更新プログラムがサービス ワーカーによってフェッチされたことを知らせる ("新しいコンテンツが利用可能です。更新してください" というメッセージを示す) と便利な場合があります 表示されます)。 このメッセージは現在、開発者の練習用に残されていますが、出発点として、[`src/registerServiceWorker.js`](src/registerServiceWorker.js) に含まれているロジックを利用できます。これは、各シナリオを検出するためにリッスンするサービス ワーカー ライフサイクル イベントを示し、既定では、適切なメッセージを JavaScript コンソールに記録するだけです。

1. 既定では、生成されたサービス ワーカー ファイルで、HTTP [API 要求](#integrating-with-an-api-backend)、イメージ、または別のドメインから読み込まれた埋め込みなどのクロスオリジン トラフィックを妨害したりキャッシュしたりすることはありません。 これらの要求に対してランタイム キャッシュ戦略を使用する場合は、[`eject`](#npm-run-eject) を実行してから、[`runtimeCaching`](https://github.com/GoogleChrome/sw-precache#runtimecaching-arrayobject)
オプションを [`webpack.config.prod.js`](../config/webpack.config.prod.js) の `SWPrecacheWebpackPlugin` セクションに構成できます。

### <a name="progressive-web-app-metadata"></a>プログレッシブ Web アプリのメタデータ

既定の構成には、[`public/manifest.json`](public/manifest.json) にある Web アプリ マニフェストが含まれます。これは、Web アプリケーションに固有の詳細を使用してカスタマイズできます。

ユーザーが Android で Chrome または Firefox を使用して Web アプリをホーム画面に追加すると、[`manifest.json`](public/manifest.json) のメタデータによって、Web アプリが表示されるときに使用するアイコン、名前、およびブランド化の色が決まります。
[Web アプリ マニフェスト ガイド](https://developers.google.com/web/fundamentals/engage-and-retain/web-app-manifest/)では、各フィールドの意味と、カスタマイズがユーザーのエクスペリエンスにどのように影響するかについて、より多くのコンテキストが提供されます。

## <a name="analyzing-the-bundle-size"></a>バンドル サイズの分析

[ソース マップ エクスプローラー](https://www.npmjs.com/package/source-map-explorer)では、ソース マップを使用して JavaScript バンドルが分析されます。 これは、コードの肥大化の原因を把握するの役立ちます。

ソース マップ エクスプローラーを Create React App プロジェクトに追加するには、これらの手順に従います。

```sh
npm install --save source-map-explorer
```

`yarn` を使用することもできます。

```sh
yarn add source-map-explorer
```

その後、`package.json` で、次の行を `scripts` に追加します。

```diff
   "scripts": {
+    "analyze": "source-map-explorer build/static/js/main.*",
     "start": "react-scripts start",
     "build": "react-scripts build",
     "test": "react-scripts test --env=jsdom",
```

その後、バンドルを分析するには、運用ビルドを実行してから analyze スクリプトを実行します。

```
npm run build
npm run analyze
```

## <a name="deployment"></a>デプロイ

`npm run build` により、アプリの運用ビルドを含む `build` ディレクトリが作成されます。 任意の HTTP サーバーを設定し、サイトへの訪問者に `index.html` が提供され、`/static/js/main.<hash>.js` のような静的パスへの要求が `/static/js/main.<hash>.js` ファイルの内容と共に提供されるようにします。

### <a name="static-server"></a>静的サーバー

[Node](https://nodejs.org/) を使用している環境では、これを処理する最も簡単な方法は、[serve](https://github.com/zeit/serve) をインストールして残りを処理できるようにすることです。

```sh
npm install -g serve
serve -s build
```

上記の最後のコマンドでは、ポート **5000** の静的サイトを提供します。 多くの [serve](https://github.com/zeit/serve) の内部設定と同様に、ポートは `-p` または `--port` フラグを使用して調整できます。

このコマンドを実行して、使用可能なオプションの完全な一覧を取得します。

```sh
serve -h
```

### <a name="other-solutions"></a>その他のソリューション

運用環境で Create React App プロジェクトを実行するために、必ずしも静的サーバーは必要ありません。 これは、既存の動的なものに統合した場合と同じように正常に機能します。

[Node](https://nodejs.org/) と [Express](http://expressjs.com/) を使用したプログラムによる例を以下に示します。

```javascript
const express = require('express');
const path = require('path');
const app = express();

app.use(express.static(path.join(__dirname, 'build')));

app.get('/', function (req, res) {
  res.sendFile(path.join(__dirname, 'build', 'index.html'));
});

app.listen(9000);
```

サーバー ソフトウェアの選択は重要ではありません。 Create React App は完全にプラットフォームに依存しないため、Node を明示的に使用する必要はありません。

静的なアセットを含む `build` フォルダーは、Create React App によって生成される唯一の出力です。

しかし、クライアント側のルーティングを使用する場合、これでは十分ではありません。 シングルページ アプリの `/todos/42` のような URL をサポートする場合は、次のセクションをお読みください。

### <a name="serving-apps-with-client-side-routing"></a>クライアント側のルーティングを使用したアプリの提供

HTML5 [`pushState` 履歴 API](https://developer.mozilla.org/docs/Web/API/History_API#Adding_and_modifying_history_entries) を使用するルーター (たとえば、`browserHistory` を使用する [React ルーター](https://github.com/ReactTraining/react-router)) を内部で使う場合、多くの静的ファイル サーバーで障害が発生します。 たとえば、`/todos/42` のルートを持つ React ルーターを使用した場合、開発サーバーは適切に `localhost:3000/todos/42` に応答しますが、上記のような運用ビルドを提供する Express は応答しません。

これは、`/todos/42` に新しいページが読み込まれたときに、サーバーでファイル `build/todos/42` を探し、それが見つからないためです。 サーバーは、`index.html` を提供することで `/todos/42` に対する要求に応答するように構成する必要があります。 たとえば、パスが不明な場合に `index.html` を提供するように上記の Express の例を修正できます。

```diff
 app.use(express.static(path.join(__dirname, 'build')));

-app.get('/', function (req, res) {
+app.get('/*', function (req, res) {
   res.sendFile(path.join(__dirname, 'build', 'index.html'));
 });
```

[Apache HTTP Server](https://httpd.apache.org/) を使用している場合は、このような `public` フォルダーに `.htaccess` ファイルを作成する必要があります。

```
    Options -MultiViews
    RewriteEngine On
    RewriteCond %{REQUEST_FILENAME} !-f
    RewriteRule ^ index.html [QSA,L]
```

これは、`npm run build` の実行時に `build` フォルダーにコピーされます。 

[Apache Tomcat](http://tomcat.apache.org/) を使用している場合は、[この Stack Overflow に関する回答](https://stackoverflow.com/a/41249464/4878474)に従う必要があります。

これで `/todos/42` に対する要求が、開発と運用の両方の環境で正しく処理されるようになります。

運用ビルド上、および[サービス ワーカー](https://developers.google.com/web/fundamentals/getting-started/primers/service-workers)をサポートするブラウザーでは、サービス ワーカーによって、`index.html` のキャッシュされたコピーが提供されて、`/todos/42` のように、すべてのナビゲーション要求が自動的に処理されます。 このサービス ワーカー ナビゲーションのルーティングは、[`eject` を実行](#npm-run-eject)してから、[`navigateFallback`](https://github.com/GoogleChrome/sw-precache#navigatefallback-string)
および [`navigateFallbackWhitelist`](https://github.com/GoogleChrome/sw-precache#navigatefallbackwhitelist-arrayregexp) オプション (`SWPreachePlugin` [構成](../config/webpack.config.prod.js)のもの) を変更することで構成または無効にすることができます。

### <a name="building-for-relative-paths"></a>相対パスのビルド

既定では、アプリがサーバー ルートでホストされていることを前提として、Create React App によってビルドが生成されます。<br>
これをオーバーライドするには、`package.json` で `homepage` を指定します。以下に例を示します。

```js
  "homepage": "http://mywebsite.com/relativepath",
```

これにより、生成された HTML ファイルで使用するルート パスを Create React App で正しく推測できるようになります。

**注**:`react-router@^4` を使用している場合は、任意の `<Router>`. で `basename` プロパティを使用して、`<Link>` のルートを作成できます。<br>
詳細情報は [こちら](https://reacttraining.com/react-router/web/api/BrowserRouter/basename-string)です。<br>
<br>
次に例を示します。
```js
<BrowserRouter basename="/calendar"/>
<Link to="/today"/> // renders <a href="/calendar/today">
```

#### <a name="serving-the-same-build-from-different-paths"></a>異なるパスからの同じビルドの提供

>注: この機能は、`react-scripts@0.9.0` 以降で使用できます。

HTML5 `pushState` 履歴 API を使用していない場合、またはクライアント側ルーティングをまったく使用しない場合は、アプリの提供元の URL を指定する必要はありません。 代わりに、`package.json` にこれを配置できます。

```js
  "homepage": ".",
```

これにより、すべての資産パスが確実に `index.html` に相対的なものになります。 その後、アプリをリビルドしなくても、`http://mywebsite.com` から `http://mywebsite.com/relativepath` や `http://mywebsite.com/relative/path` に移動できるようになります。

### <a name="azure"></a>Azure

React アプリを [Microsoft Azure](https://azure.microsoft.com/) にデプロイする方法については、[この](https://medium.com/@to_pe/deploying-create-react-app-on-microsoft-azure-c0f6686a4321)ブログ記事を参照してください。

### <a name="firebase"></a>Firebase

Azure App Service への自動展開を使用する方法については、[この](https://medium.com/@strid/host-create-react-app-on-azure-986bc40d5bf2#.pycfnafbg)ブログ記事または[この](https://github.com/ulrikaugustsson/azure-appservice-static)リポジトリを参照してください。


`npm install -g firebase-tools` を実行して、Firebase CLI をインストールします (まだインストールしていない場合)。 [Firebase アカウント](https://console.firebase.google.com/)にサインアップし、新しいプロジェクトを作成します。 `firebase login` を実行して、以前に作成した Firebase アカウントでログインします。

その後、プロジェクトのルートから `firebase init` コマンドを実行します。 **[ホスティング: Firebase ホスティング サイトを構成してデプロイする]** を選択し、前の手順で作成した Firebase を選ぶ必要があります。 `database.rules.json` の作成に同意し、パブリック ディレクトリとして `build` を選び、`y` で応答することで **シングルページ アプリとして構成する** ことにも同意する必要があります。

```sh
    === Project Setup

    First, let's associate this project directory with a Firebase project.
    You can create multiple project aliases by running firebase use --add,
    but for now we'll just set up a default project.

    ? What Firebase project do you want to associate as default? Example app (example-app-fd690)

    === Database Setup

    Firebase Realtime Database Rules allow you to define how your data should be
    structured and when your data can be read from and written to.

    ? What file should be used for Database Rules? database.rules.json
    ✔  Database Rules for example-app-fd690 have been downloaded to database.rules.json.
    Future modifications to database.rules.json will update Database Rules when you run
    firebase deploy.

    === Hosting Setup

    Your public directory is the folder (relative to your project directory) that
    will contain Hosting assets to uploaded with firebase deploy. If you
    have a build process for your assets, use your build's output directory.

    ? What do you want to use as your public directory? build
    ? Configure as a single-page app (rewrite all urls to /index.html)? Yes
    ✔  Wrote build/index.html

    i  Writing configuration info to firebase.json...
    i  Writing project information to .firebaserc...

    ✔  Firebase initialization complete!
```

重要: `firebase.json` ファイルの `service-worker.js` ファイルに適した HTTP キャッシュ ヘッダーを設定する必要があります。そうしないと、最初のデプロイ後の変更を確認できなくなります ([問題 #2440](https://github.com/facebookincubator/create-react-app/issues/2440))。 次のように、`"hosting"` キー内に追加されるはずです。

```
{
  "hosting": {
    ...
    "headers": [
      {"source": "/service-worker.js", "headers": [{"key": "Cache-Control", "value": "no-cache"}]}
    ]
    ...
```

これで、`npm run build` を使用して運用ビルドを作成した後に、`firebase deploy` を実行してデプロイできます。

```sh
    === Deploying to 'example-app-fd690'...

    i  deploying database, hosting
    ✔  database: rules ready to deploy.
    i  hosting: preparing build directory for upload...
    Uploading: [==============================          ] 75%✔  hosting: build folder uploaded successfully
    ✔  hosting: 8 files uploaded successfully
    i  starting release process (may take several minutes)...

    ✔  Deploy complete!

    Project Console: https://console.firebase.google.com/project/example-app-fd690/overview
    Hosting URL: https://example-app-fd690.firebaseapp.com
```

詳細については、「[Firebase を JavaScript プロジェクトに追加する ](https://firebase.google.com/docs/web/setup)」を参照してください。

### <a name="github-pages"></a>GitHub ページ

>注: この機能は、`react-scripts@0.2.0` 以降で使用できます。

#### <a name="step-1-add-homepage-to-packagejson"></a>ステップ 1: `homepage` を `package.json` に追加しました

**以下の手順は重要です。**<br>
**スキップすると、アプリが正しくデプロイされなくなります。**

`package.json` を開き、プロジェクトの `homepage` フィールドを追加します。

```json
  "homepage": "https://myusername.github.io/my-app",
```

または GitHub のユーザー ページで、次のようにします。

```json
  "homepage": "https://myusername.github.io",
```

Create React App では `homepage` フィールドを使用して、ビルドされた HTML ファイル内のルート URL を判断します。

#### <a name="step-2-install-gh-pages-and-add-deploy-to-scripts-in-packagejson"></a>ステップ 2: `gh-pages` をインストールして `deploy` を `package.json` の `scripts` に追加する

これで、`npm run build` を実行するたびに、GitHub ページにデプロイするための手順を示すチート シートが表示されるようになります。

[https://myusername.github.io/my-app](https://myusername.github.io/my-app) で発行するには、以下を実行します。

```sh
npm install --save gh-pages
```

`yarn` を使用することもできます。

```sh
yarn add gh-pages
```

`package.json` に次のスクリプトを追加します。

```diff
  "scripts": {
+   "predeploy": "npm run build",
+   "deploy": "gh-pages -d build",
    "start": "react-scripts start",
    "build": "react-scripts build",
```

`predeploy` スクリプトは、`deploy` が実行される前に自動的に実行されます。

プロジェクト ページではなく GitHub ユーザー ページにデプロイする場合は、次の 2 つの追加の変更を行う必要があります。

1. 最初に、リポジトリのソース ブランチを **master** 以外のブランチに変更します。
1. さらに、`package.json`master **へのデプロイをプッシュするように** スクリプトを調整します。
```diff
  "scripts": {
    "predeploy": "npm run build",
-   "deploy": "gh-pages -d build",
+   "deploy": "gh-pages -b master -d build",
```

#### <a name="step-3-deploy-the-site-by-running-npm-run-deploy"></a>ステップ 3: `npm run deploy` を実行してサイトを展開する

次に、次のコマンドを実行します。

```sh
npm run deploy
```

#### <a name="step-4-ensure-your-projects-settings-use-gh-pages"></a>ステップ 4: プロジェクトの設定で、`gh-pages` を確実に使用する

最後に、GitHub プロジェクト設定の **[GitHub ページ]** オプションが `gh-pages` 分岐を使用するように設定されていることを確認します。

<img src="http://i.imgur.com/HUjEr9l.png" width="500" alt="gh-pages branch setting">

#### <a name="step-5-optionally-configure-the-domain"></a>ステップ 5: 必要に応じて、ドメインを構成する

`CNAME` ファイルを `public/` フォルダーに追加することによって、GitHub Pages でカスタム ドメインを構成できます。

#### <a name="notes-on-client-side-routing"></a>クライアント側ルーティングに関する注意事項

GitHub Pages では、内部で HTML5 `pushState` 履歴 API を使用するルーターがサポートされていません (`browserHistory` を使用する React Router など)。 この理由として、`http://user.github.io/todomvc/todos/42` のような URL に新しいページが読み込まれると (ここで、`/todos/42` はフロントエンド ルート)、`/todos/42` を認識していないために GitHub Pages サーバーから 404 が返されることが挙げられます。 GitHub Pages 上でホストされているプロジェクトにルーターを追加する場合には、次のようないくつかの解決策があります。

* HTML5 履歴 API の使用からハッシュを使用したルーティングに切り替えることができます。 React Router を使用する場合は、この効果のために、`hashHistory` に切り替えることができますが、URL はより長く、より冗長になります (たとえば、`http://user.github.io/todomvc/#/todos/42?_k=yknaj`)。 React Router でのさまざまな履歴実装の詳細については、[こちら](https://reacttraining.com/react-router/web/api/Router)をご覧ください。
* また、特殊なリダイレクト パラメーターを使用して、`index.html` ページにリダイレクトすることによって、404 を処理するように GitHub Pages に教えることもできます。 プロジェクトを展開する前に、リダイレクト コードを含む `404.html` ファイルを `build` フォルダーに追加する必要があります。また、リダイレクト パラメーターを処理するコードを `index.html` に追加する必要があります。 この手法の詳細については、[こちらのガイド](https://github.com/rafrex/spa-github-pages)を参照してください。

<<<<<<< HEAD
### <a name="heroku"></a>Heroku
=======
#### <a name="troubleshooting"></a>トラブルシューティング

##### <a name="devtty-no-such-a-device-or-address"></a>"/dev/tty: このようなデバイスまたはアドレスはありません"

展開時に `/dev/tty: No such a device or address` または同様のエラーが発生する場合は、次のことを試してください。

1. 新しい[個人用アクセス トークン](https://github.com/settings/tokens)を作成する
2. `git remote set-url origin https://<user>:<token>@github.com/<user>/<repo>` .
3. `npm run deploy again` を試してください。

### <a name="heroku"></a>[Heroku](https://www.heroku.com/)
>>>>>>> dfbc71ce2ae07547a8544cce14a1a23fac99e071

[Create React App のための Heroku ビルドパック](https://github.com/mars/create-react-app-buildpack)を使用します。<br>
手順については、「[ゼロ構成を使用した React の展開](https://blog.heroku.com/deploying-react-with-zero-configuration)」を参照してください。

#### <a name="resolving-heroku-deployment-errors"></a>Heroku 展開エラーの解決

`npm run build` はローカルで動作する場合がありますが、Heroku 経由での展開中に失敗します。 最も一般的なケースは次のとおりです。

##### <a name="module-not-found-error-cannot-resolve-file-or-directory"></a>"モジュールが見つかりません: Error:'ファイル' または 'ディレクトリ' を解決できません"

次のような内容が返された場合:

```
remote: Failed to create a production build. Reason:
remote: Module not found: Error: Cannot resolve 'file' or 'directory'
MyDirectory in /tmp/build_1234/src
```

つまり、`import` を実行するファイルまたはディレクトリの大文字小文字が、ご利用のファイル システムまたは GitHub に表示される大文字小文字と一致していることを確認する必要があります。

Linux (Heroku で使用されるオペレーティング システム) では大文字と小文字が区別されるため、これは重要です。 したがって、`MyDirectory` と `mydirectory` は 2 つの異なるディレクトリであるため、プロジェクトはローカルでビルドされますが、大文字と小文字の違いにより、Heroku リモートの `import` ステートメントが中断されます。

##### <a name="could-not-find-a-required-file"></a>"必要なファイルが見つかりませんでした。"

パッケージから必要なファイルを除外するか無視すると、次のようなエラーが表示されます。

```
remote: Could not find a required file.
remote:   Name: `index.html`
remote:   Searched in: /tmp/build_a2875fc163b209225122d68916f1d4df/public
remote:
remote: npm ERR! Linux 3.13.0-105-generic
remote: npm ERR! argv "/tmp/build_a2875fc163b209225122d68916f1d4df/.heroku/node/bin/node" "/tmp/build_a2875fc163b209225122d68916f1d4df/.heroku/node/bin/npm" "run" "build"
```

この場合は、ファイルに適切な大文字小文字が含まれていることと、ご利用のローカル `.gitignore` または `~/.gitignore_global` で無視されないことを確認してください。

### <a name="netlify"></a>Netlify

**Netlify の CDN に手動で展開するには:**

```sh
npm install netlify-cli -g
netlify deploy
```

展開するパスとして、`build` を選択します。

**継続的デリバリーをセットアップするには:**

この設定では、Git にプッシュするか、pull request を開くと、Netlify がビルドおよび展開されます。

1. [新しい netlify プロジェクトを開始する](https://app.netlify.com/signup)
2. 使用する Git ホスティング サービスを選択し、ご利用のリポジトリを選択します
3. ビルド コマンドとして `yarn build` を、発行ディレクトリとして `build` を設定します
4. [`Deploy site`] をクリックします。

**クライアント側ルーティングのサポート:**

`pushState` をサポートするには、必ず次の書き換えルールに従って `public/_redirects` ファイルを作成してください。

```
/*  /index.html  200
```

プロジェクトをビルドすると、Create React App によって、`public` フォルダーの内容がビルド出力に配置されます。

### <a name="now"></a>Now

[now](https://zeit.co/now) では、ゼロ構成の単一コマンドの展開が提供されます。 `now` を使用すると、アプリを無料で展開できます。

1. 推奨される[デスクトップ ツール](https://zeit.co/download)経由で、またはノード経由で `npm install -g now` を使用して `now` コマンドライン ツールをインストールします。

2. `npm run build` を実行してアプリをビルドします。

3. `cd build` を実行して、ビルド ディレクトリに移動します。

4. ビルド ディレクトリ内から、`now --name your-project-name` を実行します。 次のように、出力に **now.sh** のURL が表示されます。

    ```
    > Ready! https://your-project-name-tpspyhtdtk.now.sh (copied to clipboard)
    ```

    ビルドが完了したら、その URL をブラウザーに貼り付けます。展開されたアプリが表示されます。

詳細については、[こちらの記事](https://zeit.co/blog/unlimited-static)をご覧ください。

### <a name="s3-and-cloudfront"></a>S3 と CloudFront

ご自分の React アプリをアマゾン ウェブ サービス [S3](https://aws.amazon.com/s3) および [CloudFront](https://aws.amazon.com/cloudfront/) に展開する方法については、こちらの[ブログ投稿](https://medium.com/@omgwtfmarc/deploying-create-react-app-to-s3-or-cloudfront-48dae4ce0af)をご覧ください。

### <a name="surge"></a>Surge

まだ用意していない場合は、`npm install -g surge` を実行して、Surge CLI をインストールします。 `surge` コマンドを実行してログインするか、新しいアカウントを作成します。

プロジェクト パスについて尋ねられたら、必ず `build` フォルダーを指定してください。次に例を示します。

```sh
       project path: /path/to/project/build
```

HTML5 `pushState` API を使用するルーターをサポートするには、Surge に展開する前に、ご利用のビルド フォルダー内の `index.html` の名前を `200.html` に変更することをお勧めします。 これにより、[すべての URL がそのファイルに確実にフォール バックされます](https://surge.sh/help/adding-a-200-page-for-client-side-routing)。

## <a name="advanced-configuration"></a>高度な構成

シェルまたは [.env](#adding-development-environment-variables-in-env) で環境変数を設定することにより、さまざまな開発および運用環境の設定を調整できます。

変数 | 開発 | Production | 使用
:--- | :---: | :---: | :---
ブラウザー | :white_check_mark: | :x: | 既定では、Create React App によって既定のシステム ブラウザーが開かれます。macOS 上では Chrome が優先されます。 [ブラウザー](https://github.com/sindresorhus/opn#app) を指定してこの動作をオーバーライドするか、`none` に設定して完全に無効にします。 ブラウザーの起動方法をカスタマイズする必要がある場合は、代わりにノード スクリプトを指定できます。 `npm start` に渡された引数もすべてこのスクリプトに渡され、アプリで提供される URL が最後の引数になります。 スクリプトのファイル名の拡張子は `.js` とする必要があります。
HOST | :white_check_mark: | :x: | 既定では、開発 Web サーバーは `localhost` にバインドされます。 この変数を使用すれば、別のホストを指定できます。
ポート | :white_check_mark: | :x: | 既定では、開発 Web サーバーによってポート 3000 でのリッスンが試みられるか、次に使用可能なポートを試行するように求められます。 この変数を使用すれば、別のポートを指定できます。
HTTPS | :white_check_mark: | :x: | `true` に設定すると、Create React App によって開発サーバーは `https` モードで実行されます。
PUBLIC_URL | :x: | :white_check_mark: | Create React App は、アプリケーションが Web サーバーのルートまたは [`package.json` (`homepage`)](#building-for-relative-paths) で指定されたサブパスでホストされていることを前提としています。 通常、Create React App ではホスト名が無視されます。 この変数を使用すると、指定した URL (ホスト名を含む) との間でアセットを逐語的に強制参照できます。 これは、アプリケーションをホストするために CDN を使用する場合に特に便利です。
CI | :large_orange_diamond: | :white_check_mark: | `true` に設定されている場合、Create React App は警告をビルド時の失敗として扱います。 また、テスト ランナーが監視しなくなります。 ほとんどの CI では、このフラグが既定で設定されています。
REACT_EDITOR | :white_check_mark: | :x: | アプリが開発中にクラッシュした場合、クリック可能なスタック トレースのエラー オーバーレイが表示されます。 これをクリックすると、Create React App は、現在実行中のプロセスに基づいて使用中のエディターを特定し、関連するソース ファイルを開こうとします。 [任意のエディターを検出する pull request を送信する](https://github.com/facebookincubator/create-react-app/issues/2636)ことができます。 この環境変数を設定すると、自動検出が上書きされます。 これを行う場合は、[PATH](https://en.wikipedia.org/wiki/PATH_(variable)) 環境変数がエディターの bin フォルダーを指していることを確認します。 `none` に設定して、完全に無効にすることもできます。
CHOKIDAR_USEPOLLING | :white_check_mark: | :x: | `true` に設定すると、ウォッチャーが VM 内で必要に応じてポーリング モードで実行されます。 `npm start` が変更を検出しない場合は、このオプションを使用します。
GENERATE_SOURCEMAP | :x: | :white_check_mark: | `false` に設定すると、運用ビルドに対してソース マップが生成されません。 これにより、いくつかの小規模なマシンで OOM の問題が解決されます。
NODE_PATH | :white_check_mark: |  :white_check_mark: | [Node.js の`NODE_PATH`](https://nodejs.org/api/modules.html#modules_loading_from_the_global_folders) と同じですが、許可されるのは相対フォルダーだけです。 `NODE_PATH=src` を設定することによって monorepo 設定をエミュレートする場合に便利です。

## <a name="troubleshooting"></a>トラブルシューティング

### <a name="npm-start-doesnt-detect-changes"></a>`npm start` が変更を検出しない

`npm start` の実行中にファイルを保存すると、ブラウザーは更新されたコードで更新されます。<br>
これが発生しない場合は、次のいずれかの回避策を試してください。

* プロジェクトが Dropbox フォルダー内にある場合は、移動してみてください。
* ウォッチャーに `index.js` という名前のファイルが表示されず、フォルダー名によって参照されている場合は、Webpack のバグが原因で[ウォッチャーを再起動する必要があります](https://github.com/facebookincubator/create-react-app/issues/1164)。
* Vim や IntelliJ などの一部のエディターには、現在ウォッチャーを中断する "安全な書き込み" 機能があります。 これを無効にする必要があります。 「[テキスト エディターの調整](https://webpack.js.org/guides/development/#adjusting-your-text-editor)」の手順に従います。
* プロジェクト パスにかっこが含まれている場合は、これがないパスにプロジェクトを移動してみてください。 これは、[Webpack ウォッチャーのバグ](https://github.com/webpack/watchpack/issues/42)が原因です。
* Linux と macOS では、より多くのウォッチャーを許可するために[システム設定を調整する](https://github.com/webpack/docs/wiki/troubleshooting#not-enough-watchers)ことが必要になる場合があります。
* プロジェクトが (Vagrant にプロビジョニングされた) VirtualBox などの仮想マシン内で実行されている場合は、プロジェクト ディレクトリ内に `.env` ファイルが存在しない場合は作成し、それに `CHOKIDAR_USEPOLLING=true` を追加します。 これにより、次回の `npm start` の実行時に、ウォッチャーは VM 内で必要に応じてポーリング モードを使用します。

これらのソリューションのいずれもうまくいかない場合は、[このスレッド](https://github.com/facebookincubator/create-react-app/issues/659)にコメントを残してください。

### <a name="npm-test-hangs-on-macos-sierra"></a>`npm test` が macOS Sierra でハングする

`npm test` を実行し、コンソールに `react-scripts test --env=jsdom` を出力した後にコンソールがスタックした場合は、「[facebookincubator/Watchman-app # 713](https://github.com/facebookincubator/create-react-app/issues/713)」で説明されているように、[Watchman](https://facebook.github.io/watchman/) インストールに問題がある可能性があります。

最初にプロジェクトの `node_modules` を削除して、`npm install` を実行する (`yarn` を使用する場合はこれも) ことをお勧めします。 これで解決しない場合は、次のイシューに記載されている多くの回避策のいずれかを試してみてください。

* [facebook/jest#1767](https://github.com/facebook/jest/issues/1767)
* [facebook/watchman#358](https://github.com/facebook/watchman/issues/358)
* [ember-cli/ember-cli#6259](https://github.com/ember-cli/ember-cli/issues/6259)

Watchman 4.7.0 以降をインストールすると、問題が解決することが報告されています。 [Homebrew](http://brew.sh/) を使用する場合は、次のコマンドを実行して更新できます。

```
watchman shutdown-server
brew update
brew reinstall watchman
```

[その他のインストール方法](https://facebook.github.io/watchman/docs/install.html#build-install)については、Watchman のドキュメント ページを参照してください。

それでも解決しない場合は、`launchctl unload -F ~/Library/LaunchAgents/com.github.facebook.watchman.plist` を実行してみてください。

Watchman を "アンインストール" すると問題が解決されるという報告もあります。 そのため、他の解決方法がない場合は、システムから削除して、もう一度お試しください。

### <a name="npm-run-build-exits-too-early"></a>`npm run build` が早期に終了する

メモリが制限され、スワップ領域がないマシンで `npm run build` が失敗することが報告されています。これは、クラウド環境では一般的です。 小規模なプロジェクトの場合でも、このコマンドによってシステムの RAM 使用量が数百メガバイト増加することがあります。そのため、使用可能なメモリが 1 GB 未満の場合、ビルドは次のメッセージで失敗する可能性があります。

>  プロセスが早期に終了したため、ビルドに失敗しました。 これは、システムのメモリが不足しているか、プロセスで `kill -9` が呼び出された可能性があります。

プロセスを終了していないことが確実な場合は、ビルドしているマシンに[スワップ領域を追加する](https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-ubuntu-14-04)か、プロジェクトをローカルにビルドすることを検討してください。

### <a name="npm-run-build-fails-on-heroku"></a>`npm run build` が Heroku で失敗する

これは大文字と小文字を区別するファイル名の問題である可能性があります。
「[こちらのセクション](#resolving-heroku-deployment-errors)」を参照してください。

### <a name="momentjs-locales-are-missing"></a>Moment.js ロケールがない

[Moment.js](https://momentjs.com/) を使用すると、既定では英語のロケールのみが使用可能であることがわかります。 これは、ロケール ファイルが大きく、必要なのが [Moment.js によって提供されるすべてのロケール](https://momentjs.com/#multiple-locale-support)のサブセットのみであることが考えられるためです。

バンドルに特定の Moment.js ロケールを追加するには、明示的にインポートする必要があります。<br>
次に例を示します。

```js
import moment from 'moment';
import 'moment/locale/fr';
```

複数のロケールをこの方法でインポートする場合は、次のようにロケール名を含む `moment.locale()` を呼び出すことによって、後から切り替えることができます。

```js
import moment from 'moment';
import 'moment/locale/fr';
import 'moment/locale/es';

// ...

moment.locale('fr');
```

これは、以前に明示的にインポートされたロケールに対してのみ機能します。

### <a name="npm-run-build-fails-to-minify"></a>`npm run build` の縮小に失敗する

場合によっては依存しているパッケージがコンパイルを必要としたり、ブラウザー以外の環境にコードを展開したりすることがあります。<br>
これは、エコシステムでは不適切な方法と見なされるため、Create React App には緊急の回避策がありません。<br>
<br>
それを解決するには、次のようにします。
1. 依存関係のイシュー トラッカーでイシューを開き、パッケージを事前コンパイル (ES6 モジュールは保持) するように依頼します。
2. パッケージをフォークし、修正されたバージョンを自分で発行します。
3. 依存関係が十分に小さい場合は、それを `src/` フォルダーにコピーして、アプリケーション コードとして扱います。

今後、互換性のないサードパーティ モジュールの自動コンパイルが開始する可能性がありますが、現在はサポートされていません。 この方法でも、運用ビルドの速度が低下します。

## <a name="alternatives-to-ejecting"></a>Eject の代替手段

[Eject](#npm-run-eject) では何でもカスタマイズできますが、その時点から、構成とスクリプトを自分で管理する必要があります。 これは、類似したプロジェクトが多数ある場合には困難な可能性があります。 このような場合は、Eject の代わりに `react-scripts` や必要なその他のパッケージを "フォーク" することをお勧めします。 [この記事](https://auth0.com/blog/how-to-configure-create-react-app/)では、その方法について詳しく説明しています。 [このイシュー](https://github.com/facebookincubator/create-react-app/issues/682)の詳細については、こちらを参照してください。

## <a name="something-missing"></a>説明不足ですか。

このページに必要な "How To" レシピのアイデアがある場合は、[こちらでお知らせ](https://github.com/facebookincubator/create-react-app/issues)いただくか、[コントリビュート](https://github.com/facebookincubator/create-react-app/edit/master/packages/react-scripts/template/README.md)してください。
