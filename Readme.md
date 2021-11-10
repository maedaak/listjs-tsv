# List.jsとTSVによる書誌検索「１万件」サンプルページ

## サンプルサイトURL
https://maedaak.github.io/listjs-tsv/

## 概要
List.jsとTSVによる書誌1万件規模での書誌検索サイトのサンプルページである。
高速化のため書誌データをHTML中に記載するのではなく、TSVから読み込む方法をとった。

## 使用データ
NACSIS-CATの総合目録データベースのCC-BY書誌情報を使用した。
そのままだとRDFのため、大学図書館員のための図書館システム開発練習用データ( https://mbc.dl.itc.u-tokyo.ac.jp/data4librarysystem/ )の図書書誌TSVから、先頭１万件を抽出して使っている。

## 機能
- インクリメンタルサーチ
- キーワード半角スペース区切りでAND検索
- プルダウンメニューによる絞り込み（文字列中間一致で設定）
- ファジー検索(Diff Match and Patchベース)
- ヒット件数表示
- ページネーション

## メタデータの読み込み
- TSVファイルをHTMLロード時に読み込んでいる
    - d3.js https://d3js.org/ (ISC License) を使用している

## HTMLテンプレート
- List.js https://github.com/javve/list.js (MIT licence) の付属のテンプレート機能を使っている
- HTML要素のclass属性を使いデータを値にセットする

## 開発
List.jsの基本的な機能をもとに、次の作りこみを行っている。
- 大量データ対応
    - 大量リストに合わせ、ページネーション表示のパラメータ調整
    - 大量リストに合わせ、List.jsのsearchDelayパラメータの値を750に
- iOS Safari対応    
- ヒット件数の表示（可能かどうかを含め要確認）
- List.jsのfilterを使った絞り込み（書誌の言語に適用）
- List.jsのファジー検索プラグインを追加、これによりアルファベットの大文字小文字に関係なくマッチする

## 利点
- 書誌「1万件」でも高速に起動する
- List.jsを使用するため、ユーザ独自コードが少なくて済んでいる
- AND検索をサポートしている

## 難点
### List.jsのHTMLテンプレートの表現力
- HTML要素の値を設定することはできるが、属性の設定法は不明である。
- ただし、HTML要素の値をHTMLにすることで、この問題をある程度回避することはできる。
### List.jsのレコード区切り判定
- List.jsではliだけではなく、hrなどの要素もレコード区切りとみなすため、レコード中に使うことができない。
- ただし、hr要素については、p要素の外枠指定で代替することで、この問題を回避することはできる。

## 現在の開発状況
- Wiki ( https://github.com/maedaak/listjs-tsv/wiki )にあり。

## 参考
### code4lib japan 2021ライトニングトーク
- 発表資料 https://www.slideshare.net/genroku/web-listjs-jekyll-github-pages
- GitHub Pagesで作ったサンプルページ https://maedaak.github.io/listjs_jikyll-test

### 関連サイト
- List.jsのHTML内検索機能を使った書誌「１万件」検索サンプルページ
    - https://maedaak.github.io/cat10000/
- sheetdb.jsとExcelを使った簡易書誌検索サンプルページ
    - https://maedaak.github.io/sheetdb/
