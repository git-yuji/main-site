# YUYU WEB

`yuyu-web.com`のメインサイトです。プロフィール、制作物、メールチェック、技術ブログへの入口をまとめています。

## ページとサービス

| 名前 | URL | 内容 |
| --- | --- | --- |
| トップページ | [https://yuyu-web.com/](https://yuyu-web.com/) | 各ページとサービスへの入口 |
| プロフィール | [https://yuyu-web.com/about/](https://yuyu-web.com/about/) | プロフィールとサイトの技術構成 |
| 制作物 | [https://yuyu-web.com/works/](https://yuyu-web.com/works/) | 制作したWebサービスの紹介 |
| メールチェック | [https://mail.yuyu-web.com/](https://mail.yuyu-web.com/) | メールを手軽に確認するWebアプリ |
| 技術ブログ | [https://notes.yuyu-web.com/](https://notes.yuyu-web.com/) | 記事や開発記録を掲載するブログ |

## 主な機能

- 画面サイズに合わせて表示を調整するデザイン
- Vanta.jsとThree.jsを使った地球の背景アニメーション
- 端末で「視差効果を減らす」が設定されている場合の静止画表示
- プロフィール、制作物、404ページ
- canonical、`robots.txt`、`sitemap.xml`を使った検索エンジン向けの設定
- Cloudflare Workers Static Assetsを使った静的ファイルの配信

## 使用技術

| 分類 | 使用技術 | 用途 |
| --- | --- | --- |
| フレームワーク | Astro 7 | 静的なページの作成 |
| CSS | Tailwind CSS 4 | ページの見た目の調整 |
| 背景アニメーション | Vanta.js / Three.js | 地球のアニメーション表示 |
| ホスティング | Cloudflare Workers Static Assets | ビルドしたファイルの公開 |
| デプロイ | Wrangler | Cloudflareへのデプロイ |

サイトはAstroの静的出力を使います。ビルド後のファイルは`dist/`に作成されます。

## セットアップ

### 必要なもの

- Node.js 22.23.4
- npm

Node.jsのバージョンは`.nvmrc`と`.node-version`で指定しています。nvmを使う場合は、次のコマンドで準備できます。

```sh
nvm install
nvm use
npm ci
```

`package.json`の`engines.node`を満たすNode.js 24または26も使用できます。迷った場合は、上記の指定バージョンを使用してください。

### 開発サーバーの起動

```sh
npm run dev
```

起動後、[http://localhost:4321/](http://localhost:4321/)をブラウザで開きます。ファイルを変更すると表示が自動で更新されます。

## 開発・ビルドコマンド

| コマンド | 内容 |
| --- | --- |
| `npm ci` | `package-lock.json`に合わせて依存パッケージをインストールする |
| `npm run dev` | 開発サーバーを起動する |
| `npm run build` | 公開用のファイルを`dist/`に作成する |
| `npm run preview` | ビルド結果をローカルで確認する |
| `npm run deploy` | ビルド後、Cloudflare Workersへデプロイする |

ビルド結果を確認する場合は、次の順番で実行します。

```sh
npm run build
npm run preview
```

`npm run deploy`を使うには、Cloudflareへログインできる環境が必要です。

Pull Requestでは、GitHub Actionsが`npm ci`と`npm run build`を実行します。

## ディレクトリ構成

```text
main-site/
├── .github/
│   ├── dependabot.yml       # npmパッケージの更新設定
│   └── workflows/build.yml  # Pull Requestなどでビルドを確認する設定
├── public/                  # そのまま公開する画像や設定ファイル
│   ├── _redirects           # 旧ブログURLからの転送設定
│   ├── favicon.svg          # ファビコン
│   ├── globe-static.svg     # アニメーションを減らす設定向けの背景
│   ├── og-image.png         # SNS共有用の画像
│   ├── robots.txt           # 検索エンジンの巡回設定
│   └── sitemap.xml          # サイトマップ
├── src/
│   ├── components/          # 複数のページで使う部品
│   ├── data/                # サービスURLなどの共通データ
│   ├── layouts/             # ページ共通のレイアウト
│   ├── pages/               # URLごとのページ
│   │   ├── 404.astro
│   │   ├── about.astro
│   │   ├── index.astro
│   │   └── works.astro
│   └── styles/              # サイト全体のCSS
├── astro.config.mjs         # AstroとTailwind CSSの設定
├── package.json             # npmコマンドと依存パッケージ
├── tsconfig.json            # TypeScriptの設定
└── wrangler.jsonc           # Cloudflare Workersの設定
```

## 依存パッケージの更新

Dependabotがnpmパッケージの更新を月1回、日本時間9時に確認します。更新がある場合は、最大5件のPull Requestを作成します。自動ではマージしません。

DependabotのPull Requestは、次の順番で確認します。

1. 通常の機能追加や修正を先に`main`へマージする
2. DependabotのPull Requestを最新の状態にする
3. `npm run build`と画面表示を確認する
4. 問題がなければマージする

`package.json`や`package-lock.json`で競合した場合も、通常の変更を先にマージしてからDependabotのPull Requestを更新します。
