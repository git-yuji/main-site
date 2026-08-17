# YUYU WEB

`yuyu-web.com`のメインサイトです。メールチェック、技術ブログ、プロフィールへ案内する、シンプルなポータルとして運用します。

## サイト一覧

| サービス | URL | 説明 |
| --- | --- | --- |
| YUYU WEB | <https://yuyu-web.com/> | 各サービスへの入口 |
| プロフィール | <https://yuyu-web.com/about/> | プロフィールとサイトの技術構成 |
| 制作物 | <https://yuyu-web.com/works/> | 制作したWebサービスの紹介 |
| メールチェック | <https://mail.yuyu-web.com/> | メールを手軽に確認するWebアプリ |
| 技術ブログ | <https://notes.yuyu-web.com/> | 記事や開発記録を掲載するブログ |

## 特徴

- Astroによる静的サイト
- Tailwind CSSを使ったレスポンシブデザイン
- Vanta.jsとThree.jsによるGlobeアニメーション
- 動きを減らす設定に応じた静止Globeへの切り替え
- メールチェックと技術ブログを別タブで開くサービスカード
- プロフィールとサイトの技術構成を掲載するAboutページ
- サービスの目的と技術構成を紹介する制作物ページ
- 地球儀背景とトップへの導線を備えた404ページ
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

起動後、<http://localhost:4321/>を開きます。

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
│   ├── globe-static.svg # 動きを減らす設定向けの静止背景
│   ├── og-image.png     # SNS共有用の共通OGP画像
│   ├── robots.txt       # クローラー制御
│   └── sitemap.xml      # Search Consoleへ送信するサイトマップ
├── src/
│   ├── pages/
│   │   ├── 404.astro    # ページが見つからない場合の案内
│   │   ├── about.astro  # プロフィールと技術構成
│   │   ├── index.astro  # メインページとVanta.jsの設定
│   │   └── works.astro  # 制作物の紹介
│   └── styles/
│       └── global.css   # Tailwind CSSの読み込み
├── astro.config.mjs     # AstroとTailwindの設定
├── wrangler.jsonc       # Cloudflare Workersの設定
└── package.json
```
