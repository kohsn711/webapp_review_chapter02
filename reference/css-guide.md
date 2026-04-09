# CSS解説メモ

## CSSの役割

CSS は、HTML で作った骨組みに見た目を付けるための言語です。

たとえば次のようなことを決めます。

- 余白
- 色
- 枠線
- 横幅
- レイアウト

## セレクタとは何か

CSS では、どの要素に見た目を付けるかを指定してから、ルールを書きます。

たとえば:

```css
body {
  margin: 0;
}
```

この `body` がセレクタです。

## クラス指定の読み方

HTML の `class="page"` に対して、CSS では次のように書きます。

```css
.page {
  width: 960px;
}
```

先頭の `.` は「クラス」を表します。

今回よく出てくるクラス:

- `.page`
- `.site-nav`
- `.nav-links`
- `.page-header`
- `.panel`
- `.score-form`
- `.score-table`

## よく使う基本プロパティ

### `margin`

要素の外側の余白です。

### `padding`

要素の内側の余白です。

### `width`

横幅です。

### `background`

背景色や背景の見た目を決めます。

### `color`

文字色です。

### `border`

枠線です。

### `border-radius`

角を丸くします。

## 今回の CSS を上から読む

### 1. ページ全体

#### `* { box-sizing: border-box; }`

要素のサイズ計算を分かりやすくするための設定です。

これも最初は「よく入れるおまじない」くらいで大丈夫です。

#### `body`

```css
body {
  margin: 0;
  font-family: "Hiragino Sans", "Yu Gothic", sans-serif;
  background: #17131d;
  color: #fff7ea;
}
```

ページ全体の余白、文字の種類、背景、文字色を決めています。

#### `.page`

ページ全体の横幅と配置を決めています。

```css
.page {
  max-width: 960px;
  margin: 36px auto 48px;
  padding: 0 16px;
}
```

- `margin: 36px auto 48px;`
  - 上下に余白を付けて中央寄せにしています
- `max-width`
  - 広い画面でも大きくなりすぎないようにしています
- `padding`
  - 画面の左右に少し余白を入れています

### 2. ナビゲーション

#### `.site-nav`

ページ移動のためのバーです。

```css
.site-nav {
  padding: 12px 16px;
  background: #f6efe2;
  border: 3px solid #111111;
}
```

ページ移動のリンクをまとめる土台として使っています。

#### `.nav-links a`

ナビゲーションのリンクの見た目をそろえています。

`display: inline-block;` にすると、リンクに余白や枠線を付けやすくなります。

スマホでは `position: fixed;` を使って、画面下部に固定しています。

### 3. 見出し

#### `.page-header`

ページ上部の見出しエリアです。

```css
.page-header {
  background-image: url("./score-header.svg");
  background-size: cover;
}
```

- `background`
  - 背景色
- `background-image`
  - 背景画像
- `border`
  - 枠線
- `padding`
  - 内側の余白

#### `box-shadow`

影を付ける指定です。見出しを少し強調するために使っています。

### 4. パネル

#### `.panel`

登録フォームや表を囲む箱です。

```css
.panel {
  background: #f6efe2;
  border: 3px solid #111111;
  padding: 24px;
}
```

### 5. フォーム

#### `.score-form label`

ラベル文字と入力欄をまとめています。

```css
.score-form label {
  display: block;
  margin-bottom: 16px;
}
```

今回は `display: block;` と `margin-bottom` で、項目ごとの間隔を作っています。

#### `input`, `textarea`

入力欄の横幅、余白、枠線をそろえています。

#### `button`

ボタンの色、余白、枠線を決めています。

### 6. 表

#### `.score-table`

一覧ページの表を横幅いっぱいに広げています。

#### `border-collapse: collapse;`

表の線をきれいにつなげる指定です。

#### `th`, `td`

セルの余白や罫線、文字の寄せ方を決めています。

### 7. スマホ対応

#### `@media (max-width: 640px)`

画面幅が 640px 以下のときだけ適用するルールです。

これはレスポンシブ対応と呼ばれます。初回では完全理解しなくて大丈夫です。

ここでは次の調整をしています。

- ナビゲーションバーを画面下部に固定する
- 全体の余白を少し小さくする
- パネルの内側余白を少し小さくする
- 表が横にはみ出したらスクロールできるようにする

## ページごとの見方

- `index.html`
  - ナビゲーション、背景画像付きの見出し、説明文、フォームを持つ
- `records.html`
  - ナビゲーション、背景画像付きの見出し、説明文、固定データの表を持つ

## 初回での理解レベル

まずは次が分かれば十分です。

- HTML に class を付けると、CSS で見た目を変えられる
- `margin`, `padding`, `border`, `background`, `color` で基本の見た目を作れる
- 2つのHTMLファイルで同じ CSS を共通利用できる
- `box-shadow` や `@media` のような少し発展的な書き方は、意味だけ分かれば十分

## 今回の CSS で少し発展的なもの

- `background-image`
- `box-shadow`
- `@media`
- `position: fixed`

これらは初回では完全理解不要です。まずは「どこで何の見た目を決めているか」を読めるようになることを優先してください。
