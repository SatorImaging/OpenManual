---
title: "VRM Tool Kit 取扱説明書"
lang: ja
date: 2022-05-30
author:
- "Sator Imaging"
---



VRM とそれにまつわる面倒事をどうにかしよう、という Unity 向けのツールです。

VRM がパッと作れるのはモチロンですが、更新のたびに何度もシーンを作り直さなくても良い、というのが最大の特徴です。


こんな方におススメ：

- 「モデル更新のたびにVRMを作り直すのはイヤ」
- 「モデル・ボーン調整→揺れ物チェックを行ったり来たりしたい」
- 「Spring Bone が面倒でつらい」
- 「モデル上がってきたし仮でいいから演者に合わせてみたいんよ、とりあえずVRMくれ。」
- 「昨日話題に上がったやつを今日の生放送までにモデルに反映させたいんだけど？？」


VRMの作成や調整、更新を継続的、頻繁に行う場合に特に有用なツールです。



<a href="https://www.youtube.com/watch?v=Fw0f15z39R4">【YouTube】VRM Tool Kit チュートリアル<br /><img src="https://dl.dropbox.com/s/zwtjk5cuxfbade7/VRMToolKit_QuickTutorial.gif" /></a>





<!--
https://qiita.com/sator_imaging/items/91f4156216831c3760df
-->



#### VRM Tool Kit の特徴

「**VRM Tool Kit**」には、大きく分けて２つの機能があります。



<a href="https://www.youtube.com/watch?v=rK0LFGU-XIc">【YouTube】１分でわかる「VRM Tool Kit」<br /><img src="https://dl.dropbox.com/s/zvynyugz3mrnaut/VRMToolKit_1MinuteOverview.gif" /></a>





#### 👗「揺れ物セットアップ」VRM Spring Bone の一括作成・編集ツール

ボーンやコライダーなど多数のオブジェクトを一括で調整するためのツールです。

- 人型キャラクターに合わせたコライダーの作成
- 揺れ物ボーンの一括登録
- コライダーの一括編集
- 多数のボーンとコライダーの関連付け


#### ♻️「非破壊ワークフロー」作り捨てではない Unity のシーン作り


メッシュやボーン・スキニングなど、何かを更新する度にシーンを作り直さなくても良いようにするためのツールです。

- 「モデルの追加や既存モデルの更新」「ブレンドシェイプの追加・更新」「スキンウェイトの更新」等が、VRMを書き出せる状態を維持したまま可能。
- モデルのブラッシュアップと VRM セットアップ作業を並行して進めることが可能。
- ボーンの追加・削除・更新・階層構造の変更が可能。
   - 揺れ物（Spring Bone）のパラメーターだけではなく、モデルの割りやボーン数・位置の調整も含めてのトライ＆エラーを行うことが可能。


<!--
テクスチャの更新だけであれば、VRM の再セットアップ無しでファイルの上書き→VRMの再出力だけで済みますが、非破壊ワークフローによってそれがモデルデータ（Fbx）でも可能になります。
-->


<!--
- 本来なら大した作業ではないのに、モデルはそのままでテクスチャの更新だけにしよう、という後ろ向きな発想の防止。
-->






#### マニュアル

- <a href="#もくじ">VRM Tool Kit 取扱説明書（目次）</a>



#### ライセンス

個人ライセンスでのソフトウェアの利用は、団体・法人以外の個人的な用途に限り利用可能です。
ソフトウェアの解析や改変・再配布など許可のない利用は禁止されています。






#### 制作・著作

Copyright &copy;2022 Sator Imaging, all rights reserved.

VRM and UniVRM are licensed under the MIT License.





#### ダウンロード

VRM Tool Kit のダウンロードはこちら。

- [【Unity】VRM 作成用ツール「VRM Tool Kit」](https://sator-imaging.booth.pm/items/2254383)




#### 動作確認


公式の VRM ビューアーや VRM 対応ソフトウェア（PC）で書き出した VRM の動作を確認しています。

VRoid Hub 等のアップロードして利用するタイプのサービスや、スマホアプリでの動作が上手くいった＆上手くいかなかった等がありましたら、ココや Twitter（@sator_imaging）にてお知らせいただけますと！



#### 更新履歴

- 2022-05-30
   - 文言の微調整
- v1.0.1
   - VRMバージョンについての説明を追加
- v1.0.0
   - 推奨バージョン：「VRM v0.53.0」＋「Unity 2018.4.0f1」





### もくじ

- [インストール方法](#インストール方法)
   - [推奨バージョン](#推奨バージョン)
   - [macOS での VRM プレビュー](#macos-での-vrm-プレビュー)
   - [Unity Package Manager を利用する場合](#unity-package-manager-を利用する場合)
- [VRM Tool Kit 使用方法](#vrm-tool-kit-使用方法)
   - [VRM シーンの作成手順](#vrm-シーンの作成手順)
   - [揺れ物のセットアップ手順](#揺れ物のセットアップ手順)
- [リファレンス](#リファレンス)
   - [Export FBX-Linked VRM](#export-fbx-linked-vrm)
   - [Character](#character)
   - [Spring Bone](#spring-bone)
   - [Check List](#check-list)
- [VRM（UniVRM）について](#vrmunivrmについて)
- [あわせてどうぞ](#あわせてどうぞ)
- [各種ライセンス情報](#各種ライセンス情報)
   - [アリシア・ソリッド](#アリシアソリッド)
   - [ユニティちゃん](#ユニティちゃん)





## インストール方法


まず最初に VRM 作成用の Unity プロジェクトに VRM（UniVRM）のパッケージをインポートします。


### 推奨バージョン

VRM（UniVRM）のダウンロードは以下のページより行います。※ バージョンは v0.53.0 を推奨しています。

- [Release v0.53.0 · vrm-c/UniVRM](https://github.com/vrm-c/UniVRM/releases/tag/v0.53.0)
   <iframe
      class="embed-card embed-webcard"
      scrolling="no"  frameborder="0"
      style="
         display: block;  border: none;
         margin: 10px 0px;
         width: 100%; height: 155px;
         max-width: 500px;
      "
      src="https://hatenablog-parts.com/embed?url=https://github.com/vrm-c/UniVRM/releases/tag/v0.53.0">
   </iframe>



※ 推奨バージョンについては合わせてコチラもご覧ください。

- 👉 [VRMはどのバージョンを使うべき？](https://satorimaging.github.io/OpenManual/VRMToolKit/UnderstandingOSS.ja.html)
   - https://satorimaging.github.io/OpenManual/VRMToolKit/UnderstandingOSS.ja.html



--


続いて、ダウンロードした「**VRM Tool Kit**」に含まれている、`VRMToolKit-<バージョン>.unitypackage` をプロジェクトにインポートします。



--


最後に「**VRM Tool Kit**」に含まれている、非破壊ワークフローを実現する上で必要な VRM 用の更新ファイル（`UniVRM-<バージョン>_BlendShapePreviewEditor.unitypackage`）をインストールします。



> **注**： 更新ファイルをインストールしていなかったり、UniVRM v0.53.0 以外のバージョンを使用していてブレンドシェイプのプレビューが表示されない場合は、インスペクターの「Prefab」パラメーターに、`.fbx` ファイルを設定することで表示されるようになります。


※ UniVRM の更新ファイルをインストールしていない場合の使い方  
<img src="https://dl.dropbox.com/s/ne3arofgjz1a1qa/VRMToolKitManual_WorkAroundBlendShape.gif" />



### macOS での VRM プレビュー

macOS では VRM をプレビューするためのアプリが公式からは提供されていません。

macOS 上で確認する必要がある場合は、VRM ビューアーをインストールすることが出来ます。

- [VRM ビューアー for macOS - Sator Imaging - BOOTH](https://sator-imaging.booth.pm/items/1847552)  
  <img src="https://dl.dropbox.com/s/dbq85z80mmtt8sb/VRMToolKitManual_macOS.jpg" />




### Unity Package Manager を利用する場合

VRM 公式サイトから `UniVRM.asmdef-<バージョン>.unitypackage` を追加でインストールすると、「**VRM Tool Kit**」を Unity Package Manager のパッケージとして読み込むことが出来るようになります。


※ パッケージとして利用する場合は、赤線で示した UnivRM の `***.asmdef` も合わせて導入します。  
<img src="https://dl.dropbox.com/s/wq36o6mohgj60qg/VRMToolKitManual_DownloadAsmdef.png" />



上記の追加ファイルをインストールした上で、「**VRM Tool Kit**」に含まれている `VRMToolKit.asmdef.txt` というファイルを `VRMToolKit.asmdef` という名前に変更することで、パッケージとして読み込むことが出来るようになります。


パッケージとして読み込む方法は以下のマニュアルをご覧ください。

- [Installing a local package - Unity マニュアル](https://docs.unity3d.com/ja/current/Manual/upm-ui-local.html)







## VRM Tool Kit 使用方法



### VRM シーンの作成手順


VRM シーン作成手順と注意するべき点は以下の通りです。


<a href="https://www.youtube.com/watch?v=Fw0f15z39R4">【YouTube】VRM Tool Kit チュートリアル<br /><img src="https://dl.dropbox.com/s/zwtjk5cuxfbade7/VRMToolKit_QuickTutorial.gif" /></a>






- Unity の Fbx ファイルの読み込み設定で「Rig」が「Humanoid」になっているかを確認します。
   - 「Avatar Definition」の「Configure...」を開いて、Eye・Jaw に必要のないボーンがアサインされていないかを合わせて確認します。
- Fbx ファイルをシーンのヒエラルキーに追加します。
- アバターが T ポーズになっていない場合は T ポーズにします。
   - **注**：揺れ物のボーンもモデリングに合わせたままの状態ではなく、重力に従うように調整します。
   - セットアップ時のダイアログで「Auto T-Pose」選択するか、`VRM > Character > Character to T-Pose` を実行することで自動で T ポーズにすることが出来ます。
   ※これは VRM 書き出しオプションで `Force T-Pose` をオンにした時と同じ状態です。
   - **注**：ただし、VRM の提供する `Force T-Pose` を使って T ポーズにすると、腿と足は問題ないが膝のボーンだけがねじれている、など気付き辛いエラーが発生する場合があるので、おかしなところがないか必ず確認するようにします。
      - 自動で T ポーズにした後に `VRM > Character > Except for Arm & Finger Root` を実行すると、肩から手首、指の根元のボーン以外をプレハブの初期値に戻すことができます。

- アバターを選択した状態で、`VRM > Export FBX-Linked VRM` を実行します。
   ※ この段階で非破壊ワークフローのベースが出来ているので、一度 `Pose Freeze` と `Force T-Pose`（必要な場合）をオンにして、VRM 書き出しを行って問題がないか確認しておきます。

- 続いて VRM ブレンドシェイプのパラメーターを設定します。
- スプリングボーンツールを使用して揺れ物のセットアップを行います。
- `VRM Meta` にタイトルや作者の情報を設定します。


> **注**： ボーンのセットアップの状態によっては、自動 T ポーズ機能を使うと一部のボーンが曲がることがあるので必ず確認します。



※ 自動 T ポーズを調整せずにVRMを書き出して、がに股になった状態。  
<img src="https://dl.dropbox.com/s/6b33fjl45ceizre/VRMToolKit_SetupEthan.gif" />


--


VRM の基本設定は以上で終了です。


メニューの `VRM > Check List` の項目を確認してから、`.vrm` としてエクスポートします。

> **注**：VRM を書き出すときは、`Pose Freeze` と `Force T-Pose`（必要な場合）をオンにします。











### 揺れ物のセットアップ手順


揺れ物（`VRM Spring Bone`）ツールの使い方は以下の動画で確認できます。
※ 各機能の詳細は次のリファレンスの項目をご覧ください。


<a href="https://www.youtube.com/watch?v=CHUBGTQHDIs">【YouTube】VRM Tool Kit - 揺れ物セットアップツール<br /><img src="https://i.ytimg.com/vi/CHUBGTQHDIs/maxresdefault.jpg" /></a><br />





#### スプリングボーンについての確認事項



- 揺れ物のボーンをどれだけ細かくしているかによりますが、殆どのキャラの場合コリジョンの分割数はデフォルトの 0.05（5cm 毎にコライダーを作成）で十分です。

   - PC ではなくモバイル向けなら 5cm だと少し処理が重いかもしれません。適宜調整します。
   - 動画を見てわかる通り、そもそもコリジョンをいくら細かくしても揺れ物のボーンが粗いと貫通します。
   - 重要なのはコライダーの数と揺れ物の分割数のバランスです。


- VRM Spring Bone はボーン（棒状の剛体）とコライダーの正確な衝突判定をしているわけではなく、「球体コライダーの中心点から半径以内の距離にボーンのピボットが位置している」→「衝突しているということなので押し出す」という処理を行っているだけなので、神経質にこだわってもあまり結果に結びつかないことが多いです。

- 揺れ物のボーンの数とコライダーの数がバランスを保っていることの方が重要なので、一度セットアップして動かしてみてから、必要に応じて揺れ物の衝突判定箇所を増やす等を行います。

   - よって、工程の後戻りができることが重要になります。


- 衝突判定する場所を増やすだけであれば、スキニングの為のボーンを追加する必要はなく、ボーンとボーンの間にロケーターやヌル（=GameObject）を挟むだけでも問題ありません。
   - スキニング用のボーンが仕込んであるよりも精度は低いですが、腕を貫通していたものがめり込みはするが貫通はしなくはなった、程度には出来ると思います。

- PC VR 向けなど処理の負荷を考えないのであれば、コライダーもボーンも細かく入れてしまうのが早いです。

- それでも難しければ、そもそもあまり揺れないようにバネを強くするか、重力を弱くして水の中にいるような挙動に設定しめり込みや貫通が起きづらい状態にして逃げます。



> **注**： 処理負荷の関係でコライダーの数は減らしたとしても、足や手など、揺れ物から離れている部位のコライダー削除はなるべく避けたほうが良いです。
>
> 髪の毛が揺れて腕に衝突しているのを見ると、多くのユーザーや演者は手でも髪の毛を触れると思って触ろうとして、あれ突き抜けた？ となることが多いです。所詮はバーチャルか、と現実に引き戻される原因となり得ます。







## リファレンス

VRM Tool Kit をインストールすると、Unity エディターの VRM メニューに項目が追加されます。

各機能の詳細は以下の通りです。
※ 各機能は特に指定が無いかぎり、VRM アバターのルートを選択した状態で実行します。



### Export FBX-Linked VRM

Fbx キャラクターを VRM として出力できるように調整した上で、VRM のエクスポートダイアログを表示します。


※ 実行時にダイアログウインドウが表示されるので、処理内容を選択します。  
<img src="https://dl.dropbox.com/s/pom716tpgedu0c3/VRMToolKitManual_ExportFbxLinkedVRM_01.png" />



- **Auto T-Pose**： 自動で T ポーズにします。
- **Current Pose as T-Pose**： 現在のポーズを T ポーズとして扱います。


※ 初期化時は「Auto T-Pose」、更新時は「Current Pose as T-Pose」を使うのがおススメです。


### Character

キャラクターに関する機能です。


- **Character to T-Pose**

   - キャラクターを T-Pose にします。


- **Revert to Default Pose**

   - キャラクターを初期ポーズに戻します。


- **Except for Arm & Finger Root**

   - 「肩」「上腕」「前腕」「手首」「指の根元」を除いたすべてのボーンを初期ポーズに戻します。


- **Revert All Transforms to Default**

   - キャラクターのボーンだけではなく、揺れ物を含む全ての Transform を初期状態に戻します。



<!--
### Blend Shape


ブレンドシェイプに関する機能です。

- **Update Blend Shape for VRM Export**

   - VRM Blend Shape のパラメーターをエクスポート用に調整します。実行すると、Inspector を使っての調整が不可能になります。


- **Revert Blend Shape for Inspector Preview**

   - VRM Blend Shape のパラメーターを Inspector で作業できるように再調整します。
-->



### Spring Bone


「**VRM Tool Kit**」の揺れ物（`VRM Spring Bone`）に関する機能です。



※ UniVRM に含まれる `VRM Spring Bone` についての詳細は[このページ](https://vrm.dev/univrm/components/univrm_secondary/)で確認できます。







- **Spring Works**


   - Spring Bone メニューをウインドウとして開きます。<br /><img src="https://dl.dropbox.com/s/wqq5iuyxfgej7e0/VRMToolKitManual_SpringWorks.png" />


- **Add Spring Manager**
   - スプリングマネージャー（`VRM Spring Bone`）をアバターに追加します。
      ※「髪」「スカート」等、各部位ごとにマネージャーを作成するようにします。

- **Add Spring Collider to Selection**
   - 選択したオブジェクトにコライダー（`VRM Spring Bone Collider Group`）を追加します。

- **Select Colliders in Hierarchy**

   - 選択しているオブジェクトとその階層の中から、コライダーがアタッチされている GameObject を選択します。


- **Assign Bones & Colliders to Spring Manager**

   
   - 選択しているスプリングマネージャー（`VRM Spring Bone`）に、ボーンやコライダーを関連付けます。<br /><img src="https://dl.dropbox.com/s/wgb9uoui6rudtrn/VRMToolKitManual_SpringWorksAssignToManager.png" /><br />※ Spring Bone 関連コンポーネントがない GameObject がボーンとして扱われます。


- **Scale Up/Down Selected Colliders' Radii**

   - 選択している全ての Spring Bone コライダーの半径を拡大・縮小します。

- **Generate Human Colliders for Selected Animator**

   - 選択したヒューマノイドキャラクターのボーンに対してコライダー（`VRM Spring Bone Collider Group`）を追加します。
   ※ コライダーがアタッチされた `Collider__<BoneName>` と言う名前の GameObject が各ボーンの子供として追加されます。


- **Remove Null References from Hierarchy**

   - 選択しているオブジェクトとその階層のコンポーネントから、missing になっている Root Bone や Collider を取り除きます。




### Check List


エクスポート前に確認するべき項目の一覧です。

※ 各メニューは一覧表示の為だけの物で、選択しても機能しません。




--

以上です。お疲れ様でした。




## VRM（UniVRM）について


VRM と UniVRM についての詳細は、以下のページで確認できます。

- [UniVRMマニュアル](https://vrm.dev/univrm/)


- [UniVRMのコンポーネント](https://vrm.dev/univrm/components/)









## 各種ライセンス情報


この記事内で使用、改変しているデータのライセンス情報は以下の通りです。


### アリシア・ソリッド


- [ニコニ立体ちゃん特設サイト - ニコニ立体](https://3d.nicovideo.jp/alicia/)



### ユニティちゃん


この記事中で使用されているユニティちゃんは、ユニティちゃんライセンス条項の元に提供されています。



<p><img src="https://dl.dropbox.com/s/4i8qqtitrd8pxy6/Unity-chan_LogoSilhouette.png" /></p>



- [DATA DOWNLOAD-利用規約 « UNITY-CHAN! OFFICIAL WEBSITE](https://unity-chan.com/contents/guideline/)
   <iframe
      class="embed-card embed-webcard"
      scrolling="no"  frameborder="0"
      style="
         display: block;  border: none;
         margin: 10px 0px;
         width: 100%; height: 155px;
         max-width: 500px;
      "
      src="https://hatenablog-parts.com/embed?url=https://unity-chan.com/contents/guideline/">
   </iframe>
