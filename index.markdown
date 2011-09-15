---
title: 『Rails3レシピブック』サポートページ
layout: default
---

![表紙](http://www.sbcr.jp/img/t/4797363821_01.jpg)

『Rails3レシピブック』サポートページ
====================================

【 [書誌情報](#id1) | [正誤表](#id2) | [ご意見・誤記の報告等](#id9) 】

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
  <th>サイズ種別</th><td>A5/1色</td>
 </tr><tr>
  <th>ページ数</th><td>496ページ</td>
 </tr><tr>
  <th>ISBN</th><td>978-4-7973-6382-1</td>
 </tr><tr>
  <th>本体価格</th><td>3,129円(税込)</td>
 </tr><tr>
  <th>出版日</th><td>2011年7月22日</td>
 </tr><tr>
  <th>出版社紹介ページURL</th><td><a href="http://www.sbcr.jp/products/4797363821.html">http://www.sbcr.jp/products/4797363821.html</a></td>
 </tr>
</table>

正誤表(初版に含まれるもの)
---------------------------

### Recipe 001 rvmインストール方法の間違い

インストール用のコードに誤りがあり、必要なスペースが落ちてしまっていました。

#### 正

    bash < <(curl -s https://rvm.beginrescueend.com/install/rvm)

#### 誤

    bash <<(curl -s https://rvm.beginrescueend.com/install/rvm)

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

### Recipe 058 コードリスト中のORDER方向指定が小文字になっている(p.123)

ページ先頭のコードリスト中で、ORDERの方向を指定する```ASC```や```DESC```が小文字になっています。

#### 正

    Entry.order("page_view_count DESC").order("updated_at ASC")

#### 誤

    Entry.order("page_view_count desc").order("updated_at asc")

### Recipe 076 「has\_many :through関連でできること」の説明が間違っている(p.158)

「has_many :through関連でできること」で定義されるメソッドの表の直後の説明が間違っています。

#### 正

> Blogモデルではhas_many :comments, :through => :entriesと宣言しているので、Blog#commentsなどのメソッドが追加されます。

#### 誤

> Blogモデルではhas\_many :comments, :through => :blogsと宣言しているので、Blog#commentsなどのメソッドが追加されます。

### Recipe 085 楽観的ロックの例外名が間違っている(p.183)

楽観的ロックにて競合した場合に発生する例外の名前が間違っています。

#### 正

    ActiveRecord::StaleObjectError

#### 誤

    ActiveRecord::SlateObjectError

### Recipe 112 保存済みオブジェクトに対応するフォームのmethod属性が間違っている(p.257)

保存済みオブジェクトに対応するフォームの```method```属性が```put```になると説明されていますが、誤りです。

#### 正

> &lt;form&gt;タグの```action```属性が「/blogs/モデルのID」になり、HTTPメソッドを```put```に上書きするため```_method```というhiddenフィールドが生成されます。

    <form accept-charset="UTF-8" action="/blogs/2"
        class="edit_blog" id="edit_blog_2" method="post">
        <div style="margin:0;padding:0;display:inline">
          …（略）
          <input name="_method" type="hidden" value="put" />
          …（略）
        </div>
    …（略）
    </form>

#### 誤

> &lt;form&gt;タグのaction 属性が「/blogs/モデルのID」、method属性が「put」になります。

    <form accept-charset="UTF-8" action="/blogs/2"
        class="edit_blog" id="edit_blog_2" method="post">
    …（略）
    </form>

### Recipe 119 先頭のコードリストの例で、結果が出力されない(p.276)

先頭のリストのコードが、結果が出力されない問題があったり、Railsからの警告がでる書式であったりします。```form_for```メソッド、```collection_select```メソッドの両方の例で```<%= %>```であるべきところが```<% %>```になっています。

#### 正

    <%= form_for @entry do |f| %>
      # モデルオブジェクトCategoryを選択対象とするドロップダウンリストを
      # 生成する
      <%= f.collection_select(:category_id,
                             Category.all, :id, :name) %>
    <% end %>

#### 誤

    <% form_for @entry do |f| %>
      # モデルオブジェクトCategoryを選択対象とするドロップダウンリストを
      # 生成する
      <% f.collection_select(:category_id,
                             Category.all, :id, :name) %>
    <% end %>


### Recipe 171 `xhr`メソッドの引数の説明で数が間違っている(p.398)

二つ目のコードリストの前の説明文にて、`xhr`メソッドの引数が間違っています。

#### 正

> 第1引数にHTTPメソッド、第2引数にアクション名を指定します。クエリパラメータがある場合、第3引数として指定します。

#### 誤

> 第2引数にHTTPメソッド、第3引数にアクション名を指定します。クエリパラメータがある場合、第4引数として指定します。

### Recipe 131 HTML5タグの出力例が間違っている(p.302)

タグ出力メソッドの出力例に間違いがあります。

#### 正

    <%= number_field_tag 'volume', 10, :min=>"0", :max=>"30", :step=>"5" %>
    #=> <input id="volume" max="30" min="0" name="foo" step="5" type="number"
         value= "10" />
        <br />
    <%= range_field_tag 'volume2', 10, :min=>"0", :max=>"30", :step=>"5" %>
    #=> <input id="volume2" max="30" min="0" name="foo2" step="5" type="range"
         value="10" />


#### 誤

    <%= number_field_tag 'volume', 10, :min=>"0", :max=>"30", :step=>"5" %>
    #=> <input id="foo" max="30" min="0" name="foo" step="5" type="number"
         value= "10" />
        <br />
    <%= range_field_tag 'volume2', 10, :min=>"0", :max=>"30", :step=>"5" %>
    #=> <input id="foo2" max="30" min="0" name="foo2" step="5" type="range"
         value="10" />


### Recipe 186 説明の文章が間違っている(p.449)

コードリスト直下の説明にて、説明内容に誤りがあります。

#### 正

> さらに、非同期で実行したいジョブはメソッドの形にまとめます。たとえば、

#### 誤

> さらに、非同期で実行したジョブはメソッドの形にまとめます。たとえば、

### 索引 p.467にて```default_scope```の綴りに間違いがある(p.467)

索引の```default_scope```の綴りに間違いがあります。

#### 正

> ```default_scope```宣言

#### 誤

> ```default_scape```宣言

ご意見・誤記の報告等
--------------------

本書に記載されている内容に関して、「ここの記述は間違っているのでは」「ここはこうなるべきでは」といったご指摘等がある場合は、このレポジトリのissueで受け付けております。

- ご指摘一覧 [https://github.com/rails3recipebook/rails3recipebook.github.com/issues](https://github.com/rails3recipebook/rails3recipebook.github.com/issues)
- 新規登録 [https://github.com/rails3recipebook/rails3recipebook.github.com/issues/new](https://github.com/rails3recipebook/rails3recipebook.github.com/issues/new)

上記URLよりご記入いただければ幸いです。

