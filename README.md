# Lex and YACC 

This repository is learning of [Lex and YACC primer/HOWTO](http://archive.linux.or.jp/JF/JFdocs/Lex-YACC-HOWTO.html).
Original document is [here](http://ds9a.nl/lex-yacc/).

# 3. Lex 

* %{ ~ %} のセクションは直接includeされる
* %% ~ %% で定義を書く

        flex example1.l
        gcc lex.yy.c -o example1 -lfl

みたいな感じで example1 が出来る。

## 3.1 正規表現でのマッチ

マッチトークンに正規表現が使える。
ここでは直接 printf しちゃってる。

## 3.2 C のようなシンタックスをもつもう少し高度な例

# 4. YACC

## 4.1 単純な温度調整器

 * Lexer(Tokenizer) ではマッチトークンごとに定数を return するようになってる
   * example4.l
 * それぞれの Token ごとに Parser を書いて、そこで printf してる
   * example4.y

なんかサンプルコードはコピペだけじゃ動かないのでソース参照の事。

## 4.2 引数を扱えるように拡張した、温度調整器

 * lexer では yytext にマッチした文字が入る
 * lexer では数値の場合 yylval で bison 側で取得出来る値として認識させる事が出来る
 * parser では $1, $2, $3 … とルールの出現番号で yylval を取得出来るみたい 

## Resources

 * [FlexMode - EmacWiki](http://www.emacswiki.org/emacs/FlexMode)
 * [BisonMode - EmacWiki](http://www.emacswiki.org/emacs/BisonMode)
 * [bison-mode.elとflex-mode.elのURL](http://memo.udp.jp/2011/07/10/bison-mode-el-flex-mode-el-url/)
 * [CMake 2.8 Document](http://www.cmake.org/cmake/help/cmake-2-8-docs.html)