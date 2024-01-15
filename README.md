# captioning_scripts
プロジェクト非公式のキャプション込みデータセット作成支援スクリプト群です。

下のcolabボタンを押すとスクリプトが開きます。
- キャプションファイル作成支援スクリプトたち
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/nagaokayama/captioning_scripts/blob/main/Text_cordinator.ipynb)


# How to Use

- 使用にあたってgoogleアカウントが必要です

google drive、google colabの基本的な操作方法は各自調べてください。このスクリプトを使うにあたってgoogle colabへの課金はしなくても大丈夫だと思います。

基本的には使いたいセルの入力フォームを上から埋めて「セルを実行」を押せばOK

**画像ファイルに変更を伴うセルの実行はバックアップをとり注意して行ってください。バグはなるべく早期に取り除きますが画像ファイルに意図しない変更が加えられる可能性があります**

## 事前準備
google drive内のファイルを利用する場合は一番上のセル「0. ⛰google driveのファイルを使用する場合はまずこのスクリプトを実行してください」を実行してください。

google drive使用の有無に関係なく最初に一回だけ「0.🎍必要なモジュールのインポートと関数の設定」を実行してください。



## 📖画像名と共通キャプションを各行に書き込んだcsvを生成（キャプションcsv生成）

画像が入ったフォルダと、すべての画像に共通するキャプションを記入すると各横列にそれらを割り当てたcsvファイルを作ります。各種表計算アプリで読み込めます。

エクスポート時にexport_with_shiftjisのチェックをつけることでmicrosoftエクセルで開いても文字化けしなくなります。


## ✒csvファイルから各画像用キャプションテキストファイルを生成（キャプションtxt生成）
決まった形式のcsvファイル(後述)を読み込んで画像ごとのキャプションtxtに分割してくれます。生成されたtxtファイルをダウンロードして使ってください。

![image](https://github.com/nagaokayama/captioning_scripts/assets/152504610/b6b0a242-9711-4158-a692-f74ec835f001)


### 決まった形式のcsvファイルとは...
一番左の縦列に拡張子を除いた画像ファイル名、その横にキャプションが各セルにダーッと並んでる形式です。ヘッダーはありません。

「キャプションcsv生成」で生成されるcsvはこの形式に沿ったものが作られます。

![image](https://github.com/nagaokayama/captioning_scripts/assets/152504610/65bbc0a9-9909-4257-9deb-0a8af0ec31c4)


## 🎨学習に適したサイズに画像をリサイズ（かなり自己責任でお願いします）
短辺512px以上、画素数が2の20乗px（処理上は110万pxを目安にしています）を満たすようにリサイズして指定したフォルダへ新しい画像として保存します。

一応元の画像を上書きしないように簡単なセーフティーはつけていますが確実な物ではありません。画像のパックアップを取ってからご利用ください。


## 👾画像（とキャプションtxt）を100個ずつフォルダに分配する（ちょっと慎重に使ってね）
フォルダ内の画像をupload_zipの現行ルールに沿って100枚ずつ別フォルダへ分配します。

分配先に指定したフォルダの下位にサブフォルダ（sub_1, sub_2...）が作成され、ここに100枚ずつ画像がコピーされます。

画像と同名のテキストファイル（キャプションファイル）がある場合はこれも同時に分配されます。

ちょっと自己責任ですがオプションをONにすることでzipファイルの作成やコピーを作成しないこともできます。


## 📦ZIPファイルを作成
上記のファイルの分配セルからzipファイル圧縮機能を抜き出したものです。

指定したフォルダの中身をzipに圧縮します（複数フォルダ可）

複数フォルダを一度に圧縮したいときはフォルダパスを,か、で区切って記入してください

### colabの動物モード
左上メニューバーの　ツール＞設定＞その他　のコーギー/カニ/猫モードをONにするとかわいくなります。
![image](https://github.com/nagaokayama/captioning_scripts/assets/152504610/c9e85ed0-d061-4ed0-ba9d-46f31d8085a6)
![image](https://github.com/nagaokayama/captioning_scripts/assets/152504610/111834e9-06a9-4f14-89cf-f771a39c40ff)


# 修正履歴（大きなもの）

2023/12/26　画像とテキストを100ずつに分割する機能を実装

2023/12/16　画像リサイズとCSVをshiftJISで生成モードを実装

2023/12/12　モジュールインポートを分離した関係でセルレイアウトとスクリプトの実行手順がやや変化

2023/12/10  画像ファイルからCSVファイル生成セルについて、拡張子に大文字を含む画像ファイルの名前がcsvファイルにリストアップされない問題を修正

2023/12/05　空の文字列タグをキャプションテキストに書き込まないように修正
