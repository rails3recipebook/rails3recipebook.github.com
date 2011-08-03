---
title: 『Rails3レシピブック』サポートページ
layout: default
---

Rails3レシピブック 正誤表
=========================

初版に含まれるもの
------------------

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

