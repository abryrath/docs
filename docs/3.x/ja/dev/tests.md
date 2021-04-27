# テスト

[Twig に付随する](https://twig.symfony.com/doc/tests/index.html)テンプレートタグに加えて、Craft がいくつか独自のものを提供します。

| Test                                                                    | 説明                                         |
| ----------------------------------------------------------------------- | ------------------------------------------ |
| [boolean](#boolean)                                                     | 変数が PHP 定数値と同じかどうか。                        |
| [constant](https://twig.symfony.com/doc/2.x/tests/constant.html)        | 変数が別のものと同じかどうか。                            |
| [defined](https://twig.symfony.com/doc/2.x/tests/defined.html)          | 変数が定義されているかどうか。                            |
| [divisible by](https://twig.symfony.com/doc/2.x/tests/divisibleby.html) | 数値が別の数値で割り切れるかどうか。                         |
| [empty](https://twig.symfony.com/doc/2.x/tests/empty.html)              | 変数が空かどうか。                                  |
| [even](https://twig.symfony.com/doc/2.x/tests/even.html)                | 数値が偶数かどうか。                                 |
| [instance of](#instance-of)                                             | オブジェクトが名前空間や親クラスのインスタンスかどうか。               |
| [iterable](https://twig.symfony.com/doc/2.x/tests/iterable.html)        | 変数が配列、または、Traversable オブジェクトかどうか。          |
| [missing](#missing)                                                     | オブジェクトに期待されるクラスがないかどうか。                    |
| [null](https://twig.symfony.com/doc/2.x/tests/null.html)                | 変数が `null` かどうか。                           |
| [odd](https://twig.symfony.com/doc/2.x/tests/odd.html)                  | 数値が奇数かどうか。                                 |
| [same as](https://twig.symfony.com/doc/2.x/tests/sameas.html)           | Whether a variable is the same as another. |

## `boolean`

オブジェクトが別のオブジェクトまたはクラスのインスタンスかどうかを返します。

```twig
{% if myVar is boolean %}
    {{ myVar ? 'true' : 'false' }}
{% endif %}
```

## `instance of`

Returns whether an object is an instance of another object or class.

```twig
{% if element is instance of('craft\\elements\\Entry') %}
    <h1>{{ entry.title }}</h1>
{% endif %}
```

## `missing`

指定されたオブジェクトが <craft3:craft\base\MissingComponentInterface> のインスタンスかどうかを返します。 型が見つからないコンポーネントを表すために使用されるインターフェースです。

```twig
{% if field is missing %}
    <p>😱</p>
{% endif %}
```
