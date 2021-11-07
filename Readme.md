# List.jsとtsvによる書誌検索「１万件」サンプルページ

## 概要
List.jsによる書誌1万件規模での書誌検索サイトのサンプルページ。高速化のため書誌データはTSVから読み込んでいる。

## 使用データ
NACSIS-CATの総合目録データベースのCC-BY書誌情報を使用。
そのままだとRDFのため、大学図書館員のための図書館システム開発練習用データ( https://mbc.dl.itc.u-tokyo.ac.jp/data4librarysystem/ )の図書書誌TSVから、先頭１万件を抽出して使っている。

## TSVファイルの扱い
- d3.jsを使用している

## 作りこみ
現在はList.jsの基本的な機能をもとに、次の作りこみを行っている。
- ヒット件数の表示
- iOS Safari対応
- 大量リストに合わせ、ページネーション表示のパラメータ調整
- 大量リストに合わせ、searchDelay の値を750に
- ファジー検索プラグインを追加、これによりアルファベットの大文字小文字に関係なくマッチするようになった
- filterを使った絞り込み（言語に適用）

## 参考
### code4lib japan 2021ライトニングトーク
- 発表資料 https://www.slideshare.net/genroku/web-listjs-jekyll-github-pages
- GitHub Pagesで作ったサンプルページ https://maedaak.github.io/listjs_jikyll-test
