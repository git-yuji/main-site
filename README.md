# YUYU WEB

`yuyu-web.com`のメインサイトです。メールチェック、技術ブログ、プロフィールへ案内する、シンプルなポータルとして運用します。

## サイト一覧

| サービス | URL | 説明 |
| --- | --- | --- |
| YUYU WEB | <a href="https://yuyu-web.com/" target="_blank" rel="noopener noreferrer">https://yuyu-web.com/</a> | 各サービスへの入口 |
| プロフィール | <a href="https://yuyu-web.com/about/" target="_blank" rel="noopener noreferrer">https://yuyu-web.com/about/</a> | プロフィールとサイトの技術構成 |
| メールチェック | <a href="https://mail.yuyu-web.com/" target="_blank" rel="noopener noreferrer">https://mail.yuyu-web.com/</a> | メールを手軽に確認するWebアプリ |
| 技術ブログ | <a href="https://notes.yuyu-web.com/" target="_blank" rel="noopener noreferrer">https://notes.yuyu-web.com/</a> | 記事や開発記録を掲載するブログ |

## 特徴

- Astroによる静的サイト
- Tailwind CSSを使ったレスポンシブデザイン
- Vanta.jsとThree.jsによるGlobeアニメーション
- メールチェックと技術ブログを別タブで開くサービスカード
- プロフィールとサイトの技術構成を掲載するAboutページ
- Cloudflare Workers Static Assetsによる配信
- canonical、`robots.txt`、`sitemap.xml`を使った検索エンジン向け設定

## 技術構成

| 分類 | 使用技術 |
| --- | --- |
| フレームワーク | Astro |
| スタイリング | Tailwind CSS |
| 背景アニメーション | Vanta.js / Three.js |
| ホスティング | Cloudflare Workers Static Assets |
| デプロイ | Wrangler |

## ローカル開発

### 必要な環境

- Node.js
- npm

### セットアップ

```sh
npm install
npm run dev
```

起動後、<a href="http://localhost:4321/" target="_blank" rel="noopener noreferrer">http://localhost:4321/</a>を開きます。

## コマンド

| コマンド | 用途 |
| --- | --- |
| `npm run dev` | Astro開発サーバーを起動 |
| `npm run build` | 本番用ファイルを`dist/`へ生成 |
| `npm run preview` | ビルド結果をAstroでプレビュー |
| `npm run deploy` | ビルド後、Cloudflare Workersへデプロイ |

## ディレクトリ構成

```text
main-site/
├── public/
│   ├── favicon.svg      # 地球モチーフのファビコン
│   ├── robots.txt       # クローラー制御
│   └── sitemap.xml      # Search Consoleへ送信するサイトマップ
├── src/
│   ├── pages/
│   │   ├── about.astro  # プロフィールと技術構成
│   │   └── index.astro  # メインページとVanta.jsの設定
│   └── styles/
│       └── global.css   # Tailwind CSSの読み込み
├── astro.config.mjs     # AstroとTailwindの設定
├── wrangler.jsonc       # Cloudflare Workersの設定
└── package.json
```
