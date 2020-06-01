# Wordpressサイトの制作

## 導入するプラグイン

### All In One SEO Pack

[https://ja.wordpress.org/plugins/all-in-one-seo-pack/](https://ja.wordpress.org/plugins/all-in-one-seo-pack/)

固定ページや投稿に、個別のtitle、descriptionを設定するのに使用します。

### Lazy Load by WP Rocket

[https://ja.wordpress.org/plugins/rocket-lazy-load/](https://ja.wordpress.org/plugins/rocket-lazy-load/)

画像を遅延読み込みさせるために導入します。

### Duplicate Post

[https://ja.wordpress.org/plugins/duplicate-post/](https://ja.wordpress.org/plugins/duplicate-post/)

ページを複製するために導入します。

### MW WP Form

[https://ja.wordpress.org/plugins/mw-wp-form/](https://ja.wordpress.org/plugins/mw-wp-form/)

お問い合わせなどのフォームは基本こちらで実装してください。

### No Category Base (WPML)

[https://ja.wordpress.org/plugins/no-category-base-wpml/](https://ja.wordpress.org/plugins/no-category-base-wpml/)

スラッグに `/category/` を含めない時に使います。

### Advanced Custom Fields

[https://ja.wordpress.org/plugins/advanced-custom-fields/](https://ja.wordpress.org/plugins/advanced-custom-fields/)

h1の個別設定機能の実装などに使用します。

### 弊社開発のパンくずリスト

※別途ファイルを送ります

## サイトの基本設定

### トップページ用の固定ページを作成

固定ページで「新規追加」から、タイトル「トップページ」を作成してください。

その後、「設定」→「表示設定」から、「ホームページの表示」を「固定ページ」→「トップページ」に設定してください。

### パーマリンクの設定

「設定」→「パーマリンク設定」から、「基本設定」→「投稿名」に設定してください。

### functions.phpの編集

[functions-sample.php](/functions-sample.php)に記載されている内容を、サイトの `functions.php` に記述してください。

## cssの基本設定

### デバイスのbreakpointについて

breakpointは下記のサイズに合わせてください。

```
@media screen and (min-width: 1025px) {
  PC
}

@media screen and (min-width: 768px) and (max-width: 1024px) {
  タブレット
}

@media screen and (max-width: 767px) {
  SP
}
```

## 納品時にチェックすること
- google chromeのデバッグツールのコンソールでエラーが出ていないか。
