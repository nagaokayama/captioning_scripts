# captioning_scripts
プロジェクト非公式のキャプション込みデータセット作成支援スクリプト群です。

下のcolabボタンを押すとスクリプトが開きます。
- キャプションファイル作成支援スクリプトたち
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/nagaokayama/captioning_scripts/blob/main/Text_cordinator.ipynb)


# How to Use

- 使用にあたってgoogleアカウントが必要です

google drive、google colabの基本的な操作方法は各自調べてください。このスクリプトを使うにあたってgoogle colabへの課金はしなくても大丈夫だと思います。

基本的には使いたいセルの入力フォームを上から埋めて「セルを実行」を押せばOK

## 事前準備
google drive内のファイルを利用する場合は一番上のセル「0. google driveのファイルを使用する場合はまずこのスクリプトを実行してください」を実行してください。

google drive使用の有無に関係なく最初に一回だけ「0.必要なモジュールのインポートと関数の設定」を実行してください。



## 画像名と共通キャプションを各行に書き込んだcsvを生成（キャプションcsv生成）

画像が入ったフォルダと、すべての画像に共通するキャプションを記入するといい感じに割り当てたcsvファイルを作ります。表計算アプリで読み込めます。

これによって生成されるCSVファイルは文字コードがユニコードで生成されるのでエクセルで開くと大抵の場合文字化けします。

そのような時は文字コードを指定して再度開くか、メモ帳でCSVファイルを一度開きそのまま保存してからエクセルで開き直すと表示が戻る可能性があります。

![image](https://github.com/nagaokayama/captioning_scripts/assets/152504610/440fc1ce-303a-426c-81d7-ce42f63f62f8)
![image](https://github.com/nagaokayama/captioning_scripts/assets/152504610/12c6a8c5-6cec-4d36-9c7a-ccfdf9929ebb)


## csvファイルから各画像用キャプションテキストファイルを生成（キャプションtxt生成）
決まった形式のcsvファイル(後述)を読み込んで画像ごとのキャプションtxtに分割してくれます。生成されたtxtファイルをダウンロードして使ってください。
![image](https://github.com/nagaokayama/captioning_scripts/assets/152504610/ad995699-7a8d-4c66-a405-f35c61a0e048)
![image](https://github.com/nagaokayama/captioning_scripts/assets/152504610/b6b0a242-9711-4158-a692-f74ec835f001)


### 決まった形式のcsvファイルとは...
一番左の縦列に拡張子を除いた画像ファイル名、その横にキャプションが各セルにダーッと並んでる形式です。ヘッダーはありません。

「キャプションcsv生成」で生成されるcsvはこの形式に沿ったものが作られます。

文字コードがユニコードで生成されるのでエクセルで開くと文字化けします。
そのような時は文字コードを指定して再度開くか、メモ帳でCSVファイルを一度開きそのまま保存してからエクセルで開き直すと表示が戻る可能性があります。
![image](https://github.com/nagaokayama/captioning_scripts/assets/152504610/12c6a8c5-6cec-4d36-9c7a-ccfdf9929ebb)

### 動物モード
左上メニューバーの　ツール＞設定＞その他　のコーギー/カニ/猫モードをONにするとかわいくなります。
![image](https://github.com/nagaokayama/captioning_scripts/assets/152504610/c9e85ed0-d061-4ed0-ba9d-46f31d8085a6)
![image](https://github.com/nagaokayama/captioning_scripts/assets/152504610/111834e9-06a9-4f14-89cf-f771a39c40ff)


# 修正履歴（大事な奴だけ。覚えてたら書く）

2023/12/12　モジュールインポートを分離した関係でセルレイアウトとスクリプトの実行手順がやや変化

2023/12/10  画像ファイルからCSVファイル生成セルについて、拡張子に大文字を含む画像ファイルの名前がcsvファイルにリストアップされない問題を修正

2023/12/05　空の文字列タグをキャプションテキストに書き込まないように修正
