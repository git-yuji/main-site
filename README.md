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

## リンクの変更

`src/pages/index.astro` の `services` にある `href` を、実際のサブドメインへ変更してください。
