---
title: "【AE】アニメの撮影用ツール"
lang: ja
date: 2021-12-01
author:
- "Sator Imaging"
---


大判などでカット毎にコンポサイズが違う、ラインのコンポのみ２倍サイズで作業、等々、アニメ撮影特有のコンポジット（主にCG）を行う際に必要になる、最低限の機能をまとめた After Effects 用のツールです。


![](https://github.com/SatorImaging/OpenManual/raw/master/AnimeCompoToolBox/images/Stmg_AnimeCompoToolBox.png)



似たような機能を持ったツールやスクリプトは探せば見つかりますが、

- コンポサイズを変えてもレイヤー位置が揃わなかったり
- そもそも特定のコンポのみ２倍という処理に対応出来なかったり
- 処理した後に一部のレイヤーだけアウト点が途中で終わっていたり

など、特に海外製の物はアニメの撮影のことは考えていないものが多かったので、その辺りで手を煩わされることが無いようにしています。



<!--more-->


--


コレと After Effects CS6（電話すればまだ買えるらしい）、Trapcode・Optical Flare・[OLM Open Tools](https://olm.co.jp/rd/technology/tools/) があれば最低限動ける、というツールです。


コンポやフッテージの自動読み込み等はプロジェクトに依存し、ツールが用意されていることが殆どかと思いますが、コンポ・レイヤー周りの処理は何故かツールが用意されていないことが多いかと思います。

使ってみて他にコレが無いとなー、という機能があれば是非ご連絡ください。





### マニュアル

- [Anime Compo Tool Box 取扱説明書](#もくじ)



### ダウンロード

- [Sator Imaging - BOOTH](https://sator-imaging.booth.pm/items/1994425)



### 更新履歴

- v1.0.0
    - After Effects CS6 で動作確認



### ライセンス

Copyright © Sator Imaging, all rights reserved.





### もくじ



- [インストール方法](#インストール方法)
- [起動方法](#起動方法)
- [使用方法](#使用方法)
- [ツールオプション](#ツールオプション)
    - [Comp Settings](#comp-settings)
    - [Koma-uchi Time Remap](#koma-uchi-time-remap)
    - [Footage Control](#footage-control)





## インストール方法


ダウンロードした `.jsxbin` ファイルを `ScriptUI Panels` フォルダーに保存します。


After Effects CS6 の既定のインストールフォルダーはこちら。

> C:\Program Files\Adobe\Adobe After Effects CS6\Support Files\Scripts\ScriptUI Panels




## 起動方法


Anime Compo Tool Box はドッキング可能なパネルとしても、通常のウインドウとしても動作します。


`ScriptUI Panels` フォルダーにインストールすると、メインメニュー > ウインドウ > Stmg_AnimeCompoToolBox.jsxbin からドッキング可能なパネルとして使用できます。


メインメニュー > ファイル > スクリプト > スクリプトファイルを実行… から起動した場合は、通常のウインドウとして動作します。



※ ウインドウとして起動した状態  
![](https://github.com/SatorImaging/OpenManual/raw/master/AnimeCompoToolBox/images/Stmg_AnimeCompoToolBox_Window.png)




## 使用方法


Anime Compo Tool Box を使用した基本的なワークフローは、

- ベースコンポ・テンプレコンポを読み込んで（手動 or 他のツール）
- コンポで使用しているフッテージを差し替えて（手動 or 他のツール）
- コンポのサイズ・尺調整をして（**Anime Compo Tool Box**）
- タイムリマップでコマ打ち（**Anime Compo Tool Box**）

です。


※ ベースコンポ・テンプレコンポの全てのレイヤーを手動で差し替えるには、「プロジェクト」パネル内の元のフッテージに、読み込んだ新しいフッテージを Alt+ドラッグします。（「フッテージの差し替え」よりも少し楽です）



## ツールオプション

各オプションの詳細は以下の通りです。



### Comp Settings

このオプションの適用範囲は、選択しているコンポと選択しているフォルダーに含まれるすべてのコンポ（サブフォルダー含む）です。




- **Base Width / Height**  
    基本となるコンポのサイズをピクセル数で指定します。


- **Comp Name Suffix for Double Size**  
    コンポ名の最後に指定した接尾語がある場合、コンポのサイズを **Base Width / Height** で指定したサイズの 2 倍にします。  
    接尾語はコンマで区切って複数指定が可能です。（例：`x2, Line, etc`）


- **Duration (Sec / Fr / Fps)**  
    コンポの尺を設定します。  
    フレーム数は Fps を超えても良いので、24 fps で 2 秒 72 コマに設定した場合、コンポ尺は 5 秒に設定されます。


- **Layer Fit**  
    コンポ内の全てのレイヤーを新しいコンポ設定に合わせて調整します。


    - **Transform**  
        レイヤーが中央にくるように調整します。あえて中央に寄せていない、というレイヤーも一律で Position がコンポの中心点に移動します。  
        ※ Rotation / Scale / Anchor Point は変更しません。  
        　 ※ ベースコンポ・テンプレから調整する必要はないハズ…？

    - **Duration**  
        レイヤーのイン・アウト点を最大幅に設定し、スタート時間をコンポの開始時間に移動します。


    - **Solid**  
        ~~平面レイヤーのサイズをコンポサイズに合わせて更新します。~~（未実装）



- **その他に更新される設定**  
    コンポの「開始フレーム」設定が、プロジェクト設定に合わせて調整されます。  
    内部的には `.displayStartTime` プロパティーを `0` に設定して、各コンポの表示スタートフレームがプロジェクト設定に合うようにします。




- **Take Settings**  
    選択しているフッテージまたはコンポから、サイズと尺の設定を取得します。  
    ※ ２倍サイズのコンポ・フッテージを選択して実行した場合、２倍サイズがそのままコピーされます。




- **Apply to Selections**  
    選択しているコンポとフォルダーに対して新しい設定を適用します。  
    フォルダーを選択している場合は、フォルダー・サブフォルダー内の全てのコンポが対象になります。



- **?**  
    簡易ヘルプを表示します。








### Koma-uchi Time Remap

2コマ打ち、3コマ打ち等々、アニメ特有のタイムリマップアニメーションを生成します。


- **Koma**  
    n コマ打ちの設定をします。キーフレームはコンポ時間ではなくレイヤー時間を元に作成されます。



- **Remove Existing**  
    オンに設定した場合、キーフレームを生成するときに既存のキーフレームを削除します。  
    一度コマ打ちした後にキーをずらして、このオプションをオフに設定した状態で再度コマ打ちすると、　鍔迫り合いとかでプルプルするヤツ　が作れます。


- **Add**  
    設定に基づいて、選択したレイヤーに対してキーフレームを生成します。




### Footage Control


Pencil+ でレンダリングしたライン素材がカラー素材と同名で判りづらい問題の解消や、コンポのレイヤー表示を見やすくする、フッテージを AEP ファイルからの相対パスに書き換える（未実装）等を行います。

これらは AEP プロジェクト上の操作のみで、実際のファイルに変更を加えることはありません。


※ 左：Pencil+ でサブフォルダに書き出す設定をした素材　右：表示名を更新  
![](https://github.com/SatorImaging/OpenManual/raw/master/AnimeCompoToolBox/images/FootageControl_FileNameDisplay_Project.png)


※ コンポのソース名の表示も変わる  
![](https://github.com/SatorImaging/OpenManual/raw/master/AnimeCompoToolBox/images/FootageControl_FileNameDisplay_Comp.png)



- **File Name Display**  
    プロジェクト内のファイルフッテージの表示上の名前をコントロールします。  
    ここでは以下の変数が使用可能です。


    - **${.}**　フッテージファイルのディレクトリ名
    - **&dollar;{..}**　**${.}** の親ディレクトリの名前


    - **${name}**　フッテージファイルの名前部分
    - ~~**&dollar;{1} ~ ${n}**　ファイル名を「_」で分割した結果の n 番目~~（未実装）
    - ~~**&dollar;{-1} ~ ${-n}**　ファイル名を「_」で分割した結果の後ろから n 番目~~（未実装）


    - **${fr}**　フッテージのフレーム番号部分（無い場合は空白）
    - **&dollar;{.fr}**　**${fr}** の最初にドットを付ける（無い場合は空白）
    - **${ext}**　フッテージファイルの拡張子（無い場合は空白）
    - **&dollar;{.ext}**　**${ext}** の最初にドットを付ける（無い場合は空白）


- **?**  
    簡易ヘルプを表示します。



- **To Relative Path**  
    ~~各ファイルフッテージのパスを、AEP プロジェクトからの相対パスに更新します。~~（未実装）



- **Reset**  
    ファイルフッテージの表示名を AE のデフォルトに戻します。



- **Update**  
    ファイルフッテージの表示名を設定に基づいて更新します。
