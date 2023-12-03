# captioning_scripts
いくつかおいておきます

下のcolabボタンを押すとスクリプトが開きます。
- 画像ファイルからファイル名を抽出してテキストにまとめる
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/nagaokayama/captioning_scripts/blob/main/Text_cordinator.ipynb)


# How to Use
## 画像名と共通キャプションを各行に書き込んだcsvを生成（キャプションcsv生成）
画像が入ったフォルダと、すべての画像に共通するキャプションを記入するといい感じに割り当てたcsvファイルを作ります。表計算アプリで読み込めます。csvファイルが文字化けしてたらutf-8でエンコードしてもらうと治るかも
![image](https://github.com/nagaokayama/captioning_scripts/assets/152504610/440fc1ce-303a-426c-81d7-ce42f63f62f8)
![image](https://github.com/nagaokayama/captioning_scripts/assets/152504610/12c6a8c5-6cec-4d36-9c7a-ccfdf9929ebb)


## csvファイルから各画像用キャプションテキストファイルを生成（キャプションtxt生成）
決まった形式のcsvファイル(後述)を読み込んで画像ごとのキャプションtxtに分割してくれます。
![image](https://github.com/nagaokayama/captioning_scripts/assets/152504610/ad995699-7a8d-4c66-a405-f35c61a0e048)
![image](https://github.com/nagaokayama/captioning_scripts/assets/152504610/b6b0a242-9711-4158-a692-f74ec835f001)


### 決まった形式のcsvファイルとは...
一番左の縦列に拡張子を除いた画像ファイル名、その横にキャプションが各セルにダーッと並んでる形式です。ヘッダーとかはありません。
「キャプションcsv生成」で生成されるcsvはこの形式に沿ったものが作られます。
![image](https://github.com/nagaokayama/captioning_scripts/assets/152504610/12c6a8c5-6cec-4d36-9c7a-ccfdf9929ebb)
