---
title: <span>
slug: Web/HTML/Element/span
---

{{HTMLRef}}

**HTML の `<span>` 要素**は、記述コンテンツの汎用的な行内コンテナーであり、何かを表すものではありません。スタイル付けのため ({{htmlattrxref("class")}} または {{htmlattrxref("id")}} 属性を使用して)、または {{htmlattrxref("lang")}} のような属性値を共有したりするために要素をグループ化する用途で使用することができます。他に適切な意味的要素がない時にのみ使用してください。 `<span>` は {{HTMLElement("div")}} 要素ととても似ていますが、 {{HTMLElement("div")}} が[ブロックレベル要素](/ja/docs/Web/HTML/Block-level_elements)であるのに対し、 `<span>` は[インライン要素](/ja/docs/Web/HTML/Inline_elements)です。

{{EmbedInteractiveExample("pages/tabbed/span.html", "tabbed-shorter")}}

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">
        <a href="/ja/docs/Web/HTML/Content_categories">コンテンツカテゴリ</a>
      </th>
      <td>
        <a href="/ja/docs/Web/HTML/Content_categories#フローコンテンツ"
          >フローコンテンツ</a
        >,
        <a href="/ja/docs/Web/HTML/Content_categories#記述コンテンツ"
          >記述コンテンツ</a
        >
      </td>
    </tr>
    <tr>
      <th scope="row">許可されている内容</th>
      <td>
        <a href="/ja/docs/Web/HTML/Content_categories#記述コンテンツ"
          >記述コンテンツ</a
        >
      </td>
    </tr>
    <tr>
      <th scope="row">タグの省略</th>
      <td>{{no_tag_omission}}</td>
    </tr>
    <tr>
      <th scope="row">許可されている親要素</th>
      <td>
        <a href="/ja/docs/Web/HTML/Content_categories#記述コンテンツ"
          >記述コンテンツ</a
        >を受け入れるすべての要素、または<a
          href="/ja/docs/Web/HTML/Content_categories#フローコンテンツ"
          >フローコンテンツ</a
        >を受け入れるすべての要素。
      </td>
    </tr>
    <tr>
      <th scope="row">暗黙の ARIA ロール</th>
      <td>
        <a href="https://www.w3.org/TR/html-aria/#dfn-no-corresponding-role"
          >対応するロールなし</a
        >
      </td>
    </tr>
    <tr>
      <th scope="row">許可されている ARIA ロール</th>
      <td>すべて</td>
    </tr>
    <tr>
      <th scope="row">DOM インターフェイス</th>
      <td>
        {{domxref("HTMLSpanElement")}} ({{glossary("HTML5")}}
        より前は {{domxref("HTMLElement")}})
      </td>
    </tr>
  </tbody>
</table>

## 属性

この要素には[グローバル属性](/ja/docs/Web/HTML/Global_attributes)のみがあります。

## 例

### 例 1

#### HTML

```html
<p><span>Some text</span></p>
```

#### 結果

{{EmbedLiveSample('Example_1')}}

### 例 2

#### HTML

```html
<li><span>
    <a href="portfolio.html" target="_blank">See my portfolio</a>
</span></li>
```

#### CSS

```css
li span {
  background: gold;
 }
```

#### 結果

{{EmbedLiveSample('Example_2')}}

## 仕様書

| 仕様書                                                                                                                   | 状態                             | 備考                                                                                        |
| ------------------------------------------------------------------------------------------------------------------------ | -------------------------------- | ------------------------------------------------------------------------------------------- |
| {{SpecName('HTML WHATWG', 'text-level-semantics.html#the-span-element', '&lt;span&gt;')}} | {{Spec2('HTML WHATWG')}} |                                                                                             |
| {{SpecName('HTML5 W3C', 'textlevel-semantics.html#the-span-element', '&lt;span&gt;')}}     | {{Spec2('HTML5 W3C')}}     | {{glossary("DOM")}} インターフェイスを {{domxref("HTMLSpanElement")}} に変更 |
| {{SpecName('HTML4.01', 'struct/global.html#edef-SPAN', '&lt;span&gt;')}}                         | {{Spec2('HTML4.01')}}     |                                                                                             |

## ブラウザーの互換性

{{Compat("html.elements.span")}}

## 関連情報

- HTML の {{HTMLElement("div")}} 要素
