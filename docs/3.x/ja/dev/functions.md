# ファンクション

[Twig に付随する](https://twig.symfony.com/doc/functions/index.html)テンプレートファンクションに加えて、Craft がいくつか独自のものを提供します。

| Function                                                                                       | ファンクション                                                          |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------- |
| [actionInput](#actioninput)                                                                    | 不可視項目の `action` を出力します。                                          |
| [actionUrl](#actionurl)                                                                        | コントローラーのアクション URL を生成します。                                        |
| [alias](#alias)                                                                                | 文字列をエイリアスとして解析します。                                               |
| [attr](#attr)                                                                                  | HTML 属性を生成します。                                                   |
| [attribute](https://twig.symfony.com/doc/2.x/functions/attribute.html)                         | 変数の動的属性にアクセスします。                                                 |
| [beginBody](#beginbody)                                                                        | 「begin body」に登録されたスクリプトやスタイルを出力します。                              |
| [block](https://twig.symfony.com/doc/2.x/functions/block.html)                                 | ブロックの出力をプリントします。                                                 |
| [ceil](#ceil)                                                                                  | Rounds a number up.                                              |
| [className](#classname)                                                                        | 指定されたオブジェクトの完全修飾クラス名を返します。                                       |
| [clone](#clone)                                                                                | オブジェクトを複製します。                                                    |
| [combine](#combine)                                                                            | 2つの配列を1つに結合します。                                                  |
| [configure](#configure)                                                                        | 渡されたオブジェクトに属性をセットします。                                            |
| [constant](https://twig.symfony.com/doc/2.x/functions/constant.html)                           | 指定された文字列の定数値を返します。                                               |
| [create](#create)                                                                              | 新しいオブジェクトを作成します。                                                 |
| [csrfInput](#csrfinput)                                                                        | 不可視項目の CSRF トークンを返します。                                           |
| [cpUrl](#cpurl)                                                                                | コントロールパネルの URL を生成します。                                           |
| [cycle](https://twig.symfony.com/doc/2.x/functions/cycle.html)                                 | 値の配列を循環します。                                                      |
| [dataUrl](#dataurl)                                                                            | Outputs an asset or file as a base64-encoded data URL.           |
| [date](https://twig.symfony.com/doc/2.x/functions/date.html)                                   | 日付を作成します。                                                        |
| [dump](https://twig.symfony.com/doc/2.x/functions/dump.html)                                   | 変数に関する情報をダンプします。                                                 |
| [endBody](#endbody)                                                                            | 「end body」に登録されたスクリプトやスタイルを出力します。                                |
| [expression](#expression)                                                                      | データベース式オブジェクトを作成します。                                             |
| [floor](#floor)                                                                                | 整数値に切り上げます。                                                      |
| [getenv](#getenv)                                                                              | 環境変数の値を返します。                                                     |
| [gql](#gql)                                                                                    | スキーマ全体に対して、GraphQL クエリを実行します。                                    |
| [head](#head)                                                                                  | 「head」に登録されたスクリプトやスタイルを出力します。                                    |
| [hiddenInput](#hiddeninput)                                                                    | 不可視項目を出力します。                                                     |
| [include](https://twig.symfony.com/doc/2.x/functions/include.html)                             | レンダリングされたテンプレートのコンテンツを返します。                                      |
| [input](#input)                                                                                | HTML input タグを出力します。                                             |
| [max](https://twig.symfony.com/doc/2.x/functions/max.html)                                     | 配列内の最大値を返します。                                                    |
| [min](https://twig.symfony.com/doc/2.x/functions/min.html)                                     | 配列内の最小値を返します。                                                    |
| [ol](#ol)                                                                                      | 整数の等差数列を含むリストを返します。                                              |
| [parent](https://twig.symfony.com/doc/2.x/functions/parent.html)                               | 親ブロックの出力を返します。                                                   |
| [parseEnv](#parseenv)                                                                          | 文字列を環境変数、または、エイリアスとして解析します。                                      |
| [plugin](#plugin)                                                                              | ハンドルに従ってプラグインのインスタンスを返します。                                       |
| [random](https://twig.symfony.com/doc/2.x/functions/random.html)                               | ランダムな値を返します。                                                     |
| [range](https://twig.symfony.com/doc/2.x/functions/range.html)                                 | Returns a list containing an arithmetic progression of integers. |
| [raw](#raw)                                                                                    | 出力時に HTML エンコードされないよう、指定された文字列を`Twig\Markup` オブジェクトで囲みます。       |
| [redirectInput](#redirectinput)                                                                | 不可視項目の `redirect` を出力します。                                        |
| [seq](#seq)                                                                                    | シーケンスの次、または、現在の番号を出力します。                                         |
| [shuffle](#shuffle)                                                                            | Randomizes the order of the items in an array.                   |
| [siteUrl](#siteurl)                                                                            | フロントエンドの URL を生成します。                                             |
| [svg](#svg)                                                                                    | SVG 文書を出力します。                                                    |
| [source](https://twig.symfony.com/doc/2.x/functions/source.html)                               | レンダリングせずに、テンプレートのコンテンツを返します。                                     |
| [tag](#tag)                                                                                    | HTML タグを出力します。                                                   |
| [template_from_string](https://twig.symfony.com/doc/2.x/functions/template_from_string.html) | 文字列からテンプレートを読み込みます。                                              |
| [ul](#ul)                                                                                      | Outputs an array of items as an unordered list.                  |
| [url](#url)                                                                                    | Generates a URL.                                                 |

## `actionInput( actionPath )`

特定のコントローラーやアクションのための POST リクエストをルーティングするために使用される不可視項目を出力するためのショートカット。 これは、テンプレート内に直接 `<input type="hidden" name="action" value="controller/action-name">` を書き込むのと実質的に同じです。

```twig
<form method="POST">
    {{ actionInput('users/save-user') }}<!-- ...
```

オプションで、引数 `options` を渡すことにより、タグに追加の属性をセットできます。

```twig
{{ actionInput('users/save-user', {
    id: 'action-input'
}) }}
```

## `alias( string )`

相対形式と絶対形式、および、アクティブな <config3:actionTrigger> 設定を自動的に考慮し、コントローラーアクションの URL を返します。

### 引数

整数値に切り上げます。

- **`path`** – 結果となる URL がサイトで指すべきパス。 それは、ベースサイト URL に追加されます。
- **`params`** – URL に追加するクエリ文字列パラメータ。 これは文字列（例：`'foo=1&bar=2'`）またはオブジェクト（例：`{foo:'1', bar:'2'}`）が利用可能です。
- **`scheme`** – URL が使用するスキーム（`'http'` または `'https'`）。 デフォルト値は、現在のリクエストが SSL 経由で配信されているかどうかに依存します。 そうでなければ、サイト URL のスキームが使用され、SSL 経由なら `https` が使用されます。

## `beginBody()`

その文字列が[エイリアス](https://www.yiiframework.com/doc/guide/2.0/en/concept-aliases)ではじまるかをチェックする [Craft::getAlias()](yii2:yii\BaseYii::getAlias()) に、文字列を渡します。 （詳細については、[コンフィギュレーション](../config/README.md#aliases)を参照してください。 ）

```twig
<img src="{{ alias('@assetBaseUrl/images/logo.png') }}">
```

## `ceil( num )`

指定されたオブジェクトのクローンを作成します。

```twig
{{ ceil(42.1) }} → 43
```

## `className( object )`

「begin body」に登録されたスクリプトやスタイルを出力します。 `<body>` タグの直後に配置する必要があります。

```twig
<body>
    {{ beginBody() }}

    <h1>{{ page.name }}</h1>
    {{ page.body }}
</body>
```

## `clone( object )`

ブロックの出力をプリントします。

Twig コアの [`block`](https://twig.symfony.com/doc/2.x/functions/block.html) ファンクションと同様に機能します。

## `create( type )`

整数値に切り上げます。

```twig
{# Pass in a class name #}
{% set cookie = create('yii\\web\\Cookie') %}

{# Or a full object configuration array #}
{% set cookie = create({
    class: 'yii\\web\\cookie',
    name: 'foo',
    value: 'bar'
}) %}
```

## `csrfInput()`

整数値に切り捨てます。

```twig
{% set class = className(entry) %}
{# Result: 'craft\\elements\\Entry' #}
```

## `endBody()`

環境変数の値を返します。

```twig
{% set query = craft.entries.section('news') %}
{% set articles = clone(query).type('articles') %}
```

## `expression( expression, params, config )`

文字列が環境変数（`$VARIABLE_NAME`）、および / または、エイリアス（`@aliasName`）を参照しているかどうかを確認し、参照されている値を返します。

```twig
{{ floor(42.9) }} → 42
```

## `floor( num )`

[`Yii::configure()`](yii2:yii\BaseYii::configure()) から継承された `Craft::configure()` メソッドの振る舞いを渡します。 オブジェクトに属性を適用するという点で [`create`](#create) に似ていますが、新しいインスタンスを作成する代わりに、既存のオブジェクトを受け入れて変更します。

```twig
{# Modify an `EntryQuery` object set up by a relational field: #}
{% set myRelatedEntries = configure(entry.myEntriesField, {
    section: 'blog'
}).all() %}
```

[`merge`](https://twig.symfony.com/doc/2.x/filters/merge.html) フィルタの代わりに利用することもできます。

```twig
{% set myObject = { one: 'Original' } %}
{# With `merge`: #}
{% set myObject = myObject | merge({ one: 'Overridden', two: 'New' }) %}

{# With `configure`: #}
{% do configure(myObject, { one: 'Overridden', two: 'New' }) %}
```

あまり良いアイデアではありませんが、技術的にはモデルやエレメントの属性をセットするために利用することもできます。

```twig
{% do configure(entry, { title: 'New Title' }) %}
{% do craft.app.elements.saveElement(entry) %}
```

## `constant`

指定された文字列の定数値を返します。

Twig コアの [`constant`](https://twig.symfony.com/doc/2.x/functions/constant.html) ファンクションと同様に機能します。

## `create`

与えられたクラス名やオブジェクト設定に基づいて新しいオブジェクトインスタンスを作成します。 サポートされる引数の詳細については、<yii2:Yii::createObject()> を参照してください。

```twig
{# Pass in a class name #}
{% set cookie = create('yii\\web\\Cookie') %}

{# Or a full object configuration hash #}
{% set cookie = create({
    class: 'yii\\web\\cookie',
    name: 'foo',
    value: 'bar'
}) %}
```

## `cpUrl`

相対形式と絶対形式、および、アクティブな <config3:cpTrigger> 設定を自動的に考慮し、コントロールパネルの URL を返します。

```twig
<a href="{{ cpUrl('settings') }}">Visit control panel settings</a>
```

### 引数

`siteUrl()` ファンクションは、次の引数を持っています。

- **`path`** – 結果となる URL がサイトで指すべきパス。 それは、ベースサイト URL に追加されます。
- **`params`** – URL に追加するクエリ文字列パラメータ。 これは文字列（例：`'foo=1&bar=2'`）またはオブジェクト（例：`{foo:'1', bar:'2'}`）が利用可能です。
- **`scheme`** – URL が使用するスキーム（`'http'` または `'https'`）。 デフォルト値は、現在のリクエストが SSL 経由で配信されているかどうかに依存します。 そうでなければ、サイト URL のスキームが使用され、SSL 経由なら `https` が使用されます。

## `csrfInput`

不可視の CSRF トークン入力欄を返します。 CSRF 保護が有効になっているすべてのサイトでは、POST 経由で送信するそれぞれのフォームにこれを含めなければなりません。

```twig
{{ csrfInput() }}
```

オプションで、引数 `options` を渡すことにより、タグに追加の属性をセットできます。

```twig
{{ csrfInput({
    id: 'csrf-input'
}) }}
```

## `dataUrl`

Outputs an asset or file as a base64-encoded [data URL](https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/Data_URIs). You can pass it an <craft3:craft\elements\Asset> object or a file path (optionally using an [alias](../config/#aliases)).

```twig
{# Asset object `myLogoAsset` #}
<img src="{{ dataUrl(myLogoAsset) }}" />

{# File path, optionally using an alias #}
<img src="{{ dataUrl('@webroot/images/my-logo-asset.svg') }}" />

{# Output: <img src="data:image/svg+xml;base64,PHN2ZyBoZWlnaHQ9IjEwMCIgdmd(...)" /> #}
```

データベースクエリで使用するための新しい <yii2:yii\db\Expression> オブジェクトを作成して返します。

- **`mustShowScriptName`** – ここに `true` がセットされている場合、「index.php」を含めた URL が返され、コンフィグ設定
- **`mimeType`** - Optional MIME type. If omitted, the file’s MIME type will be determined automatically.

## `endBody`

「end body」に登録されたスクリプトやスタイルを出力します。 `</body>` タグの直前に配置する必要があります。

```twig
<body>
    <h1>{{ page.name }}</h1>
    {{ page.body }}

    {{ endBody() }}
</body>
```

## `expression`

環境変数の値を返します。

```twig
{% set entries = craft.entries()
    .andWhere(expression('[[authorId]] = :authorId', {authorId: currentUser.id}))
    .all() %}
```

## `floor`

スキーマ全体に対して、GraphQL クエリを実行します。

```twig
{{ floor(42.9) }}
{# Output: 42 #}
```

## `getenv`

文字列が環境変数（`$VARIABLE_NAME`）、および / または、エイリアス（`@aliasName`）を参照しているかどうかを確認し、参照されている値を返します。

```twig
{{ getenv('MAPS_API_KEY') }}
```

## `gql`

Executes a GraphQL query against the full schema.

```twig
{% set result = gql('{
  entries (section: "news", limit: 2, orderBy: "dateCreated DESC") {
    postDate @formatDateTime (format: "Y-m-d")
    title
    url
    ... on news_article_Entry {
      shortDescription
      featuredImage {
        url @transform (width: 300, immediately: true)
        altText
      }
    }
  }
}') %}

{% for entry in result.data %}
    <h3><a href="{{ entry.url }}">{{ entry.title }}</a></h3>
    <p class="timestamp">{{ entry.postDate }}</p>

    {% set image = entry.featuredImage[0] %}
    <img class="thumb" src="{{ image.url }}" alt="{{ image.altText }}">

    {{ entry.shortDescription|markdown }}
    <p><a href="{{ entry.url }}">Continue reading… </a></p>
{% endfor %}
```

## `head`

「head」に登録されたスクリプトやスタイルを出力します。 `</head>` タグの直前に配置する必要があります。

```twig
<head>
    <title>{{ siteName }}</title>
    {{ head() }}
</head>
```

## `hiddenInput`

オプションで、引数 `options` を渡すことにより、タグに追加の属性をセットできます。

```twig
{{ hiddenInput('entryId', entry.id) }}
{# Output: <input type="hidden" name="entryId" value="100"> #}
```

レンダリングされたテンプレートのコンテンツを返します。

```twig
{{ hiddenInput('entryId', entry.id, {
    id: 'entry-id-input'
}) }}
```

## `include`

Twig コアの [`include`](https://twig.symfony.com/doc/2.x/functions/include.html) ファンクションと同様に機能します。

HTML input タグを出力します。

## `input`

オプションで、引数 `options` を渡すことにより、タグに追加の属性をセットできます。

```twig
{{ input('email', 'email-input', '') }}
{# Output: <input type="email" name="email-input" value=""> #}
```

配列内の最大値を返します。

```twig
{{ input('email', 'email-input', '', {
    id: 'custom-input'
}) }}
```

## `max`

Twig コアの [`max`](https://twig.symfony.com/doc/2.x/functions/max.html) ファンクションと同様に機能します。

配列内の最小値を返します。

## `min`

Twig コアの [`min`](https://twig.symfony.com/doc/2.x/functions/min.html) ファンクションと同様に機能します。

This works identically to Twig’s core [`min`](https://twig.symfony.com/doc/2.x/functions/min.html) function.

## `ol`

出力時に HTML エンコードされないよう、指定された文字列を`Twig\Markup` オブジェクトで囲みます。

```twig
{% set titles = craft.entries()
    .section('news')
    .select('title')
    .column() %}
{{ ol(titles) }}
{# Output:
<ol>
    <li>Shocking Foo</li>
    <li>You Won’t Believe This Bar</li>
    <li>Ten Baz You Can’t Live Without</li>
</ol>
#}
```

### 引数

`url()` ファンクションは、次の引数を持っています。

- **`siteId`** – URL が指すべきサイト ID。 デフォルトでは、現在のサイトが使用されます。
- **`params`** – An attributes argument where each key+value will be set as attributes on the `<ol>`, with the exception of two special options:
    - **`encode: false`** – Prevents the list items from being HTML-encoded.
    - **`itemOptions: {...}`** – Tag attributes to be applied to each of the `<li>`s.

## `parseEnv`

`<input type="hidden" name="redirect" value="{{ url|hash }}">` を入力するためのショートカットです。

## `plugin`

オプションで、引数 `options` を渡すことにより、タグに追加の属性をセットできます。

```twig
{{ plugin('commerce').version }}
```

## `raw`

`name` で定義されたシーケンスの次または現在の番号を出力します。

```twig
{% set html = raw('<p>Don’t encode me.</p>') %}
{{ html }}
```

::: tip
これは、変数が他のテンプレート/マクロに渡された場合でも Twig が HTML をエスケープしないことを覚えている点を除き、[raw](https://twig.symfony.com/doc/2.x/filters/raw.html) フィルタと同様に機能します。
:::

## `redirectInput`

オプションで特定の長さにゼロ詰めした数値にできます。

```twig
{{ redirectInput(url) }}
```

インクリメントせずにシーケンスの現在の数字を表示するには、引数 `next` に `false` をセットします。

```twig
{{ redirectInput(url, {
    id: 'redirect-input'
}) }}
```

## `seq`

配列内のエレメントの順序をランダム化します。

```twig
<p>This entry has been read {{ seq('hits:' ~ entry.id) }} times.</p>
```

サイト上のページへの URL を作成するため _だけ_ という点を除けば、[url()](#url-path-params-scheme-mustshowscriptname) と似ています。

`siteUrl()` ファンクションは、次の引数を持っています。

```twig
{{ now|date('Y') ~ '-' ~ seq('orderNumber:' ~ now|date('Y'), 5) }}
{# outputs: 2018-00001 #}
```

SVG 文書を出力します。

```twig
<h5><a href="{{ entry.url }}">{{ entry.title }}</a></h5>
<p>{{ seq('hits:' ~ entry.id, next=false) }} views</p>
```

## `shuffle`

次のものを渡すことができます。

```twig
{% set promos = craft.entries.section('promos').all() %}
{% set shuffledPromos = shuffle(promos) %}

{% for promo in shuffledPromos %}
    <div class="promo {{ promo.slug }}">
        <h3>{{ promo.title }}</h3>
        <p>{{ promo.description }}</p>
        <a class="cta" href="{{ promo.ctaUrl }}">{{ promo.ctaLabel }}</a>
    </div>
{% endfor %}
```

## `siteUrl`

Similar to [url()](#url-path-params-scheme-mustshowscriptname), except _only_ for creating URLs to pages on your site.

```twig
<a href="{{ siteUrl('company/contact') }}">Contact Us</a>
```

### 引数

[attr](filters.md#attr) フィルタを利用して、ルートの `<svg>` ノードに追加する独自の class 名を指定することもできます。

- **`path`** – 結果となる URL がサイトで指すべきパス。 それは、ベースサイト URL に追加されます。
- **`params`** –  URL に追加するクエリ文字列パラメータ。 これは文字列（例：`'foo=1&bar=2'`）または、[ハッシュ](twig-primer.md#hashes)（例：`{foo:'1', bar:'2'}`）が利用可能です。
- **`scheme`** – URL が使用するスキーム（`'http'` または `'https'`）。 デフォルト値は、現在のリクエストが SSL 経由で配信されているかどうかに依存します。 そうでなければ、サイト URL のスキームが使用され、SSL 経由なら `https` が使用されます。
- **`path`** – 結果となる URL がサイトで指すべきパス。 それは、ベースサイト URL に追加されます。

## `svg`

レンダリングせずに、テンプレートのコンテンツを返します。

Twig コアの [`source`](https://twig.symfony.com/doc/2.x/functions/source.html) ファンクションと同様に機能します。

- SVG ファイルのパス。

  ```twig
  {{ svg('@webroot/icons/lemon.svg') }}
  ```

- [アセットフィールド](../assets-fields.md)から引っ張られたような、<craft3:craft\elements\Asset> オブジェクト。

  ```twig
  {% set image = entry.myAssetsField.one() %}
   {% if image and image.extension == 'svg' %}
     {{ svg(image) }}
   {% endif %}
  ```

- 生の SVG マークアップ。

  ```twig
  {% set image = include('_includes/icons/lemon.svg') %}
   {{ svg(image) }}
  ```

ファンクションにアセットまたは生のマークアップを渡した場合、デフォルトでは SVG は [svg-sanitizer](https://github.com/darylldoyle/svg-sanitizer) を利用して潜在的に悪意のあるスクリプトをサニタイズし、ドキュメント内の ID や class 名が DOM の他の ID や class 名と衝突しないよう名前空間を付加します。 引数 `sanitize`、および、`namespace` を利用して、これらの動作を無効にできます。

```twig
{{ svg(image, sanitize=false, namespace=false) }}
```

属性引数に `text` が含まれる場合、その値は HTML エンコードされ、タグのテキストコンテンツとしてセットされます。

```twig
{{ svg('@webroot/icons/lemon.svg')|attr({ class: 'lemon-icon' }) }}
```

## `source`

属性引数に `html` が含まれている（かつ、`text` が含まれていない）場合、その値はタグのインナー HTML としてセットされます（HTML エンコードされません）。

第二引数に渡される他のすべてのキーは、<yii2:yii\helpers\BaseHtml::renderTagAttributes()> を利用してタグの属性としてセットされます。

## `tag`

属性が `true` にセットされている場合、値なしで追加されます。

```twig
{{ tag('div', {
    class: 'foo'
}) }}
{# Output: <div class="foo"></div> #}
```

`null` または `false` をセットされた属性は、省略されます。

```twig
{{ tag('div', {
    text: 'Hello'
}) }}
{# Output: <div>Hello</div> #}
```

URL を返します。

::: warning
Be sure you trust any input you provide via `html` since it could be an XSS (cross-site scripting) attack vector. It’s safer to use `text` wherever possible.
:::

```twig
{{ tag('div', {
    html: 'Hello<br>world'
}) }}
{# Output: <div>Hello<br>world</div> #}
```

::: tip
クエリ文字列パラメータを追加、および / または、絶対 URL にスキームを適用するために、`url()` ファンクションを使用することができます。

If an attribute is set to `true`, it will be added without a value.

```twig
{{ tag('input', {
    id: "foo",
    name: "bar",
    required: true
}) }}
{# Output: <input id="foo" name="bar" required> #}
```

Any attribute set to `null` or `false` will be omitted.

## `ul`

配列内のアイテムの順番をランダム化します。

```twig
{% set titles = craft.entries()
    .section('news')
    .select('title')
    .column() %}
{{ ul(titles) }}
{# Output:
<ul>
    <li>Shocking Foo</li>
    <li>You Won’t Believe This Bar</li>
    <li>Ten Baz You Can’t Live Without</li>
</ul>
#}
```

### Arguments

The `ul()` function has the following arguments:

- **`items`** – An array of items to be wrapped in `<li>`s. These will be HTML-encoded by default.
- **`params`** – An attributes argument where each key+value will be set as attributes on the `<ul>`, with the exception of two special options:
    - **`encode: false`** – Prevents the list items from being HTML-encoded.
    - **`itemOptions: {...}`** – Tag attributes to be applied to each of the `<li>`s.

## `url`

URL を生成します。

```twig
<a href="{{ url('company/contact') }}">Contact Us</a>
```

### Arguments

The `url()` function has the following arguments:

- **`path`** – The path that the resulting URL should point to on your site. It will be appended to your base site URL.
- **`params`** –  URL に追加するクエリ文字列パラメータ。 これは文字列（例：`'foo=1&bar=2'`）または、[ハッシュ](twig-primer.md#hashes)（例：`{foo:'1', bar:'2'}`）が利用可能です。
- **`scheme`** – URL が使用するスキーム（`'http'` または `'https'`）。 デフォルト値は、現在のリクエストが SSL 経由で配信されているかどうかに依存します。 そうでなければ、サイト URL のスキームが使用され、SSL 経由なら `https` が使用されます。
- **`mustShowScriptName`** – If this is set to `true`, then the URL returned will include “index.php”, disregarding the <config3:omitScriptNameInUrls> config setting. （ブラウザのアドレスバーに表示されない URL と .htaccess ファイルのリダイレクトとの衝突を避けたいような、Ajax 経由の POST リクエストで使用される URL の場合に有用です。 ）

Using the `url()` function has advantages over hard-coding URLs in your templates:

- Generated URLs will encourage consistency by respecting settings like [addTrailingSlashesToUrls](config3:addTrailingSlashesToUrls).
- Your site will be more portable, making it easier to do something like move to a new domain or subdomain.
- If the page has a `token` URL parameter, that token will automatically get appended to generated URLs to maintain preview context navigating around the site.

::: tip
You can use the `url()` function for appending query string parameters and/or enforcing a scheme on an absolute URL:
```twig
{{ url('http://my-project.com', 'foo=1', 'https') }}
{# Outputs: "https://my-project.com?foo=1" #}
```
:::
