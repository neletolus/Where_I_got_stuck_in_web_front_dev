# LIFFメモ

## target=_blankをつけないとリンクが開かない。
詳しくは理解していないので後で調査が必要だが、WebView内で直接リンクにアクセスすることができないようなので、
target=_blankが必要。  
（LIFFの設定次第かもしれない...？）
<br />
<br />
<br />

## 実行環境
横着して最新のnodeLTSで使っても動かない。  
liffは2年前で開発が止まっているので、  
最高でも  
- node
  - 18.17.1
- Yarn
  - 1.22.19

あたりにすると安心。
<br />
<br />
<br />

## デバッグ環境
liff実機デバッグで検索すると出てくるliff-inspectorは多分動かない。  
https://github.com/line/liff-inspector/blob/main/README_ja.md  

vConsoleを使おう  
https://github.com/Tencent/vConsole