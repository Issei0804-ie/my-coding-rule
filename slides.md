---
theme: seriph
class: text-center
highlighter: shiki
lineNumbers: false
drawings:
  persist: false
transition: slide-left
title: コーディングの時に気をつけているルール
mdc: true
addons:
  - '@katzumi/slidev-addon-qrcode'
  - slidev-addon-components
  - slidev-addon-rabbit
---
# コーディングの時に気をつけているルール

## issei

<!-- v0.0.1 -->

---

# 目次

- そのロジック、コメントを書くかメソッドにするか
- 驚き最小の法則

---

# そのロジック、コメントを書くかメソッドにするか

- この処理どう思います？🤔

```
// ここの上にも処理がいっぱいある

public function show(Article $article) {
  $responseBody = [];

  if ($article->updated_at > $article->created_at) {
    $responseBody['isEdited'] = true;
  }

  // その他の処理が書いてある
  // ...

  return $responseBody;
}
```

---

# そのロジック、コメントを書くかメソッドにするか

<style>
.red-code {
  color: red;
}
</style>

- この処理どう思います？🤔

<pre><code>
// ここの上にも処理がいっぱいある

public function show(Article $article) {
  $responseBody = [];

  if (<span class="red-code">$article->updated_at > $article->created_at</span>) {
    $responseBody['isEdited'] = true;
  }

  // その他の処理が書いてある
  // ...

  return $responseBody;
}
</code></pre>

--- 

```php
// ここの上にも処理がいっぱいある

public function show(Article $article) {
  $responseBody = [];

  <span style="color: red;">if ($article->updated_at > $article->created_at) { // [!code focus:3 red]
    $responseBody['isEdited'] = true;
  }</span>

  // その他の処理が書いてある
  // ...

  return $responseBody;
}
```