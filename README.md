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

## 依存関係のメンテナンス

Dependabotを使い、npmパッケージの更新を月1回、日本時間9時に確認します。更新がある場合は最大5件までPull Requestを作成します。自動マージは行いません。

`main`へのマージが多い場合も、Dependabotは更新された`main`を基準にPull Requestを更新します。`package.json`や`package-lock.json`で競合した場合は、通常の機能追加や修正を先にマージしてからDependabotのPull Requestを更新します。

DependabotのPull Requestは、次の順番で確認します。

1. 通常の機能追加・修正を先に`main`へマージする
2. DependabotのPull Requestを最新化する
3. `npm run build`と画面表示を確認する
4. 問題がなければDependabotのPull Requestをマージする

## ディレクトリ構成

```text
main-site/
├── .github/
│   └── dependabot.yml   # npm依存関係の定期更新設定
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
