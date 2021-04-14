# README

## セットアップ

サイト作成

```shell
hugo new site hugo-imperfect-slim-contentful
```

レポジトリ初期化

```shell
cd hugo-future-imperfect-slim-contentful
git init
echo '*~' >> .gitignore
echo '*.bak' >> .gitignore
echo '*.orig' >> .gitignore
echo '.env' >> .gitignore
echo 'public' >> .gitignore
echo 'resources' >> .gitignore
```

テーマ設定(submoduleはhttpsプロトコルで追加)

```shell
git submodule add https://github.com/pacollins/hugo-future-imperfect-slim.git themes/future-imperfect-slim
```

(参考)submoduleの削除

```shell
git submodule deinit -f themes/future-imperfect-slim
git rm themes/future-imperfect-slim
rm -fr .git/modules/future-imperfect-slim
```

サイト設定

```shell
cp themes/future-imperfect-slim/exampleSite/config.toml .
```

config.toml

```toml
baseURL = "https://example.com/"
languageCode = "en-us"
defaultContentLanguage = "ja"
title = "My New Hugo Site"
theme = "future-imperfect-slim"
```

> github pagesやnetlifyで使う場合はbaseURLのプロトコルはhttpsにすること

起動確認(http://localhost:1313)

```shell
cp /path/to/someplace/Makefile .
make run
```

### Contentfulとの連携

package.json

```json
{
  "name": "my-hugo-project",
  "scripts": {
    "dev": "contentful-hugo --preview && hugo server",
    "build": "contentful-hugo && hugo --minify"
  }
}
```

```shell
npm i -S contentful-hugo
contentful-hugo --init
```

上記で作成された`contentful-hugo.config.js`をカスタマイズする

### Github

Githubレポジトリ作成後

```shell
git remote add origin git@github.com:toyoakekaki/hugo-future-imperfect-slim-contentful.git
git add .
git commit -m 'first commit'
git branch -M main
git push -u origin main
```

## 使い方

### 投稿

新規投稿

```shell
hugo new posts/2020/05/helloworld.md
content/posts/2020/05/helloworld.md created
```

```shell
SLUG=helloworld DATE=20200505 make post
```

文書作成

```shell
vi content/posts/2020/05/helloworld.md
```

下書きモード解除

```shell
vi content/posts/2020/05/helloworld.md
draft: false
```

## 注意

メディアファイル(css/js)を/から参照するのでnetlifyやgithub pagesのproject向き(github pagesのuserはだめ)

## Link

* [Hugo Theme Dream \| Hugo Themes](https://themes.gohugo.io/hugo-theme-dream/)
