# 作業開始時にGIで対応する項目

- サーバーの用意
- デザインファイルの用意
- 移行する記事の確認
- メタタグの発注
- アナリティクスタグの発行
- 問い合わせフォームの完了ページの文言、自動返信メールの文言、管理者当てメールの文言、送信先などの確認

# wordpressサイトの制作用件

## バージョンなどについて

基本的にはwordpress本体、プラグインは最新バージョンで構築してください。

## プラグイン関連

### サイト構築時に導入するプラグイン

#### All In One SEO Pack

[https://ja.wordpress.org/plugins/all-in-one-seo-pack/](https://ja.wordpress.org/plugins/all-in-one-seo-pack/)

固定ページや投稿に、個別のtitle、descriptionを設定するのに使用します。

#### Lazy Load by WP Rocket

[https://ja.wordpress.org/plugins/rocket-lazy-load/](https://ja.wordpress.org/plugins/rocket-lazy-load/)

画像を遅延読み込みさせるために導入します。

#### Duplicate Post

[https://ja.wordpress.org/plugins/duplicate-post/](https://ja.wordpress.org/plugins/duplicate-post/)

ページを複製するために導入します。

#### MW WP Form

[https://ja.wordpress.org/plugins/mw-wp-form/](https://ja.wordpress.org/plugins/mw-wp-form/)

お問い合わせなどのフォームは基本こちらで実装してください。

#### No Category Base (WPML)

[https://ja.wordpress.org/plugins/no-category-base-wpml/](https://ja.wordpress.org/plugins/no-category-base-wpml/)

スラッグに `/category/` を含めない時に使います。

#### Advanced Custom Fields

[https://ja.wordpress.org/plugins/advanced-custom-fields/](https://ja.wordpress.org/plugins/advanced-custom-fields/)

h1の個別設定機能の実装などに使用します。

#### gicp-breadcrumbs（弊社開発のパンくずリスト）

※別途ファイルを送ります

### プラグインの設定

#### gicp-breadcrumbs（弊社開発のパンくずリスト）

プラグインを有効化した後に、wordpressの管理画面にある左メニューバーに `設定` → `パンくず設定` が追加されます。

パンくずを表示させるには下記のコードを表示させる場所に記述してください。

`<?php get_gi_breadcrumbs(); ?>`

※プラグインが出力するcssを使用せずに、独自でレイアウトしていただいて構いません。

※プラグイン起因で起こったバグなどに関しては納品後に弊社で対応致しますのでご報告ください。

## サイトの基本設定

### トップページ用の固定ページを作成

固定ページで「新規追加」から、タイトル「トップページ」を作成してください。

その後、「設定」→「表示設定」から、「ホームページの表示」を「固定ページ」→「トップページ」に設定してください。

### パーマリンクの設定

「設定」→「パーマリンク設定」から、「基本設定」→「投稿名」に設定してください。

### functions.phpの編集

下記のコードをwordpressの `functions.php` に記述してください。

```
remove_action('wp_head', 'print_emoji_detection_script', 7);
remove_action('wp_print_styles', 'print_emoji_styles');
remove_action('wp_head', 'wp_generator');
remove_action('wp_head', 'wp_shortlink_wp_head');
remove_action('wp_head', 'rsd_link');
remove_action('wp_head', 'wlwmanifest_link');
remove_filter('the_content', 'wpautop');
remove_filter('the_excerpt', 'wpautop');
remove_action('load-update-core.php', 'wp_update_themes');
remove_action('wp_head', 'adjacent_posts_rel_link_wp_head');

function remove_dns_prefetch($hints, $relation_type) {
  if ( 'dns-prefetch' === $relation_type ) {
    return array_diff( wp_dependencies_unique_hosts(), $hints );
  }
  return $hints;
}
add_filter('wp_resource_hints', 'remove_dns_prefetch', 10, 2);

```

### 不要なソースの削除

テーマに不要なソースコードは全て削除してください。

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

## 制作していく上での注意点

### basic認証を掛けてください。

サーバーにアップロードする際はbasic認証を設定してください。

### javascriptは `</body>` 直前に書いててください。

サイト高速化の観点から、基本的にはjavascriptをヘッダーには書かず、 `</body>` の直前に書くようにしてください。

### 画像に `alt` を入れられるようにしておいてください。

cssの `background-image` を使用せず、なるべくhtmlのimgタグで画像を出力し、altを設定出来るようにしてください。

※`background-attachment: fixed;` を使う場合や、工数が跳ね上がる場合は無理してimgタグにしなくて大丈夫です。

wordpressにアップロードされた画像（アイキャッチや記事など）のaltには、`代替テキスト` が入るようにしてください。

### h1の設定

ヘッダーの上部にh1タグを設定してください。

### 画像の書き出しについて

画像の最大表示領域の2倍のサイズで書き出してください。

## 納品時にチェックすること

- google chromeのデバッグツールのコンソールでエラーが出ていないか。

## 納品後にGIで対応すること

- h1を個別で設定出来るようにする
- alt、メタタグの設定
- 画像の圧縮
- キャッシュ設定
- パスワードの変更
- ssl化

