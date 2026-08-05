# Main Site

AstroとVanta.jsのGlobeエフェクトを使った、サービス案内用のメインサイトです。

## ローカル起動

```sh
npm install
npm run dev
```

起動後、`http://localhost:4321` を開きます。

## Cloudflare Workersへデプロイ

```sh
npm run deploy
```

`/blog`と`/about`は、Cloudflare Workers上でトップページへ301リダイレクトされます。

## Search Console

Search Consoleにはドメインプロパティ`yuyu-web.com`を登録し、Cloudflare DNSのTXTレコードで所有権を確認します。確認後、`https://yuyu-web.com/sitemap.xml`を送信してください。

## リンクの変更

`src/pages/index.astro` の `services` にある `href` を、実際のサブドメインへ変更してください。
