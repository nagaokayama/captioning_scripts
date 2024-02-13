# captioning_scripts
プロジェクト非公式のキャプション込み画像データ作成支援スクリプトです。

画像ファイルを元にキャプションtextの作成を容易にするcsvファイルを生成します。

csvファイルはエクセルといった表計算ソフトで読み込めるファイル形式です。テキストファイルを一つずつ編集するより一覧性が高く、表計算ソフト独自の便利な機能を使うことでキャプション付けの速度向上が可能です。

同一ではないが類似したキャプションを持つ大量の画像に対して特に効果的です。

下のcolabボタンを押すとスクリプトが開きます。

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/nagaokayama/captioning_scripts/blob/main/Text_cordinator.ipynb)



# 簡単な使い方の説明
基本的には作業に応じて上のセルから順番に実行していくことになります。

Googleドライブに画像ファイルをアップロード

画像が入っているフォルダを指定して共通キャプションを記入してcsvを生成（＆ダウンロード）

csvファイルでキャプションを編集

編集したcsvをgoogle driveにアップロードし、これをもとにしてキャプションが記入されたテキストファイルを生成

テキストファイルを（zipに圧縮して）ダウンロード

画像とテキストファイルをまとめてzipに圧縮した場合、そのzipはそのままupload_zipで投稿できます

___

# How to Use

- このプログラムの使用にあたってはgoogleアカウントが必要です

google drive、google colabの基本的な操作方法は各自調べてください。このスクリプトを使うにあたってgoogle colabへの課金は必要ありません。

基本的には使いたいセルの入力フォームを上から埋めて「セルを実行」を押せばOK

**画像ファイルへの変更を伴うセルの実行はバックアップをとり注意して行ってください。バグはなるべく早期に取り除きますが画像ファイルに意図しない変更が加えられる可能性があります**

## 事前準備

あらかじめ Google driveに画像ファイルをフォルダにまとめてアップロードしておくと作業がスムーズになります。（zipファイル可）

google drive内のファイルを利用する場合は一番上のセル「0. ⛰google driveのファイルを使用する場合はまずこのスクリプトを実行してください」を実行してください。

google drive使用の有無に関係なく**最初に一回だけ**「0.🎍必要なモジュールのインポートと関数の設定」を実行してください。



## 📖画像名と共通キャプションを各行に書き込んだcsvを生成（キャプションcsv生成）

画像が入ったフォルダと、すべての画像に共通するキャプションを記入すると左端の縦列に画像名、各横列にキャプションを割り当てたcsvファイルを作ります。生成したcsvは各種表計算アプリで読み込めます。

エクスポート時にexport_with_shiftjisのチェックをつけることでmicrosoftエクセルで開いても文字化けしなくなります。
![image](https://github.com/nagaokayama/captioning_scripts/assets/152504610/79e9251f-ba77-4f28-a103-da3d71b19dbf)


## ✒csvファイルから各画像用キャプションテキストファイルを生成（キャプションtxt生成）
決まった形式のcsvファイル(後述)を読み込んで画像ごとのキャプションtxtに分割してくれます。生成されたtxtファイルをダウンロードして使ってください。

前述のセルで生成したcsvに限らず、形式が揃ってさえいればどのようなcsvでも読み込むことができます
![image](https://github.com/nagaokayama/captioning_scripts/assets/152504610/b6b0a242-9711-4158-a692-f74ec835f001)


### 決まった形式のcsvファイルとは...
一番左の縦列に拡張子を除いた画像ファイル名、その横にキャプションが各セルにダーッと並んでる形式です。ヘッダーはありません。

「キャプションcsv生成」で生成されるcsvはこの形式に沿ったものが作られます。

![image](https://github.com/nagaokayama/captioning_scripts/assets/152504610/65bbc0a9-9909-4257-9deb-0a8af0ec31c4)


## 🎨学習に適したサイズに画像をリサイズ（かなり自己責任でお願いします）
mitsua likesにアップロードする画像の最低サイズとモデルの学習に十分な解像度の両方を満たすように画像をリサイズします。

具体的には短辺512px以上、画素数が2の20乗px（処理上は110万pxを目安にしています）を両方満たすように拡大もしくは縮小して指定したフォルダへ新しい画像として保存します。

一応元の画像を上書きしないように簡単なセーフティーはつけていますが確実な物ではありません。画像のバックアップを取ってからご利用ください。

このリサイズ処理を通すことでファイルサイズが小さくなるので最大枚数の100枚でzipにまとめてもファイルサイズがたいていの場合discordのアップロード上限サイズ内に収まる利点もあります。

## 👾画像（とキャプションtxt）を100個ずつフォルダに分配する（ちょっと慎重に使ってね）
フォルダ内の画像をupload_zipの現行ルールに沿って100枚ずつ別フォルダへ分配します。

分配先に指定したフォルダの下位にサブフォルダ（sub_1, sub_2...）が作成され、ここに100枚ずつ画像がコピーされます。

画像と同名のテキストファイル（キャプションファイル）がある場合はこれも同時に分配されます。

ちょっと自己責任ですがオプションをONにすることで分配と同時にzipファイルを作成したり画像とテキストのコピーを残さないこともできます。
![image](https://github.com/nagaokayama/captioning_scripts/assets/152504610/f6f34565-f04f-4bb3-beb2-cf9347b6a75e)


## 📦ZIPファイルを展開/ZIPファイルを作成
指定したフォルダの中身をzipに圧縮もしくは指定したzipファイルを展開します

複数フォルダを一度に圧縮したいときはフォルダパスを,か、で区切って記入してください

## おまけ　google colabの動物モード
左上メニューバーの　ツール＞設定＞その他　のコーギー/カニ/猫モードをONにするとかわいくなります。
![image](https://github.com/nagaokayama/captioning_scripts/assets/152504610/c9e85ed0-d061-4ed0-ba9d-46f31d8085a6)
![image](https://github.com/nagaokayama/captioning_scripts/assets/152504610/111834e9-06a9-4f14-89cf-f771a39c40ff)

# よくある質問

# 修正履歴（大きなもの）
2024/02/12  hiec画像の読み込みに対応、リサイズ時のexifによる画像の回転を抑制

2024/1/ ZIPの展開・圧縮を行えるセルを追加しました

2023/12/26　画像とテキストを100ずつに分割する機能を実装

2023/12/16　画像リサイズとCSVをshiftJISで生成モードを実装

2023/12/12　モジュールインポートを分離した関係でセルレイアウトとスクリプトの実行手順がやや変化

2023/12/10  画像ファイルからCSVファイル生成セルについて、拡張子に大文字を含む画像ファイルの名前がcsvファイルにリストアップされない問題を修正

2023/12/05　空の文字列タグをキャプションテキストに書き込まないように修正
