---
title: 『Rails3レシピブック』サポートページ
layout: default
---

『Rails3レシピブック』サポートページ
====================================

![表紙](http://www.sbcr.jp/img/t/4797363821_01.jpg)

Ruby on Railsの定番リファレンスとして好評を博したレシピブックが、装いも新たにRails 3版として登場。日本のRails開発の第一人者である松田明氏を加え、Rails 3.1に世界最速対応いたしました。定番からRails 3系の新機能まで、これからのRailsの使い方がわかります。

書誌情報
--------

<table>
 <tr>
  <th>タイトル</th><td>『Rail3レシピブック 190の技』</td>
 </tr><tr>
  <th>出版社</th><td>ソフトバンククリエイティブ</td>
 </tr><tr>
  <th>著者</th><td>高橋征義／松田明／諸橋恭介著</td>
 </tr><tr>
  <th>サイズ種別</th><td>A5/2色</td>
 </tr><tr>
  <th>ページ数</th><td>496ページ</td>
 </tr><tr>
  <th>ISBN</th><td>978-4797363821</td>
 </tr><tr>
  <th>本体価格</th><td>2,00円(税込み2,940円)</td>
 </tr><tr>
  <th>出版日</th><td>2011年7月25日</td>
 </tr><tr>
  <th>出版社紹介ページURL</th><td>http://www.sbcr.jp/products/4797363821.html</td>
 </tr>
</table>

正誤表(初版に含まれるもの)
---------------------------

### Recipe 021 `default_url_options`と`include`の順が逆(p.43)

一つ目のコードリスト `app/models/social_service.rb` に誤りがありました。
`default_url_options`を設定する前に、無名モジュールを`include`する必要があります。

#### 正

    class SocialService
      include Rails.application.routes.url_helpers
      self.default_url_options = {:host => 'www.example.com'}
    end

#### 誤

    class SocialService
      self.default_url_options = {:host => 'www.example.com'}
      include Rails.application.routes.url_helpers
    end

### Recipe 036 `params`で取得するパラメータの出力例が間違っている(p.74)

最後のコードリストの、`params`メソッドの出力例が間違っています。

#### 正

    params #=> { "args"=>["v1", "v2", "v3"], "commit"=>"commit" }

#### 誤

    params #=> { "args"=>["value_1", "v2", "v3"], "commit"=>"commit" }

### Recipe 171 `xhr`メソッドの引数の説明で数が間違っている(p.398)

二つ目のコードリストの前の説明文にて、`xhr`メソッドの引数が間違っています。

#### 正

> 第1引数にHTTPメソッド、第2引数にアクション名を指定します。クエリパラメータがある場合、第3引数として指定します。

#### 誤

> 第2引数にHTTPメソッド、第3引数にアクション名を指定します。クエリパラメータがある場合、第4引数として指定します。


ご意見・誤記の報告等
--------------------

本書に記載されている内容に関して、「ここの記述は間違っているのでは」「ここはこうなるべきでは」といったご指摘等がある場合は、このレポジトリのissueで受け付けております。

- ご指摘一覧 https://github.com/rails3recipebook/rails3recipebook.github.com/issues
- 新規登録 https://github.com/rails3recipebook/rails3recipebook.github.com/issues/new

上記URLよりご記入いただければ幸いです。
