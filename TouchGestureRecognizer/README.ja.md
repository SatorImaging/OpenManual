<p><a href="https://t.co/MplSzYxEX2?amp=1"><img src="https://dl.dropbox.com/s/bwnlx3zkvmu80zc/UnityTouchGestureRecognizer_Logo__1200x630.jpg" /></a></p>






- [使い方](#使い方)
    - [タップ判定の閾値](#タップ判定の閾値)
    - [タップ判定](#タップ判定)
    - [タッチしている指の数](#タッチしている指の数)
    - [UnityEngine.Touch](#unityenginetouch)
    - [タッチの継続時間](#タッチの継続時間)
    - [ジェスチャー](#ジェスチャー)
        - [スワイプ](#スワイプ)
        - [フリック](#フリック)
        - [ピンチ（拡大・縮小）](#ピンチ拡大縮小)
        - [ピンチ（回転）](#ピンチ回転)
        - [ピンチ（スワイプ）](#ピンチスワイプ)






[Touch Gesture Recognition for Unity - YouTube](https://www.youtube.com/watch?v=I5CWLGUljsk)<br />
<a href="https://www.youtube.com/watch?v=I5CWLGUljsk"><img src="https://i.ytimg.com/vi/I5CWLGUljsk/mqdefault.jpg" /></a><br />




## 使い方

`using SatorImaging.UnityTouchRecognizer;` する。

TouchRecognizer に初めてアクセスしたときに初期化されるが、必要に応じて `TouchRecognizer.Initialize()` で明示的にイニシャライズする。

MonoBehaviour の Update() 内などで、`TouchRecognizer.Update()` を毎フレーム呼ぶ。


> ※ 今時点で `.Update()` は、同一フレーム内で何回呼ばれても一度しか更新しない。という処理はしていないので、複数の場所で `.Update()` しない。






### タップ判定の閾値

時間の閾値のみでタップ距離の閾値は無し。`.Get***()` で距離や角度の閾値を指定出来るので必要であれば。

- `TouchRecognizer.tapCountTimeThreshold`
    - タップの判定の閾値（秒）
- `TouchRecognizer.tapCountIntervalTimeThreshold`
    - 複数回タップの判定になる、各タップの間隔（秒）



### タップ判定

- `TouchRecognizer.IsTapped`
    - タップ判定されたフレームでオンに。
- `TouchRecognizer.TapCount`
    - タップの回数。インターバルの閾値次第でどんどん増えていく。
- `TouchRecognizer.TapFingerCount`
    - タップ判定された時の指の数。2 本の指でタッチした状態で片方の指でタップをした場合は 2 となる。ピンチジェスチャーに割り当てた画面回転などのアクションをリセットするときに使う。



### タッチしている指の数

- `TouchRecognizer.FingerCount`
    - 現在タッチしている指の数。
- `TouchRecognizer.IsFingerCountChanged`
    - 指の数が変わったフレームでオンに。
- `TouchRecognizer.IsFingerCountIncreased`
    - 指数が増えたフレームでオンに。
- `TouchRecognizer.IsFingerCountDecreased`
    - 指数が減ったフレームでオンに。



### UnityEngine.Touch

タッチしていないときは `TouchRecognizer.nullTouch` が返ってくる。`0 > Touch.fingerId` なら nullTouch。

- `TouchRecognizer.FirstFinger`
    - UnityEngine.Touch を直接見たい場合。
    - Touch.fingerId を追っかけてるので場合によっては `.SecondFinger` は存在して `.FirstFinger` は `.nullTouch` の場合アリ。
- `TouchRecognizer.SecondFinger`
    - UnityEngine.Touch を直接見たい場合。



### タッチの継続時間

- `TouchRecognizer.TouchDuration`
    - タッチの継続時間（秒）
- `TouchRecognizer.LatestTouchDuration`
    - 最新のタッチの継続時間（秒）。指数が減った場合は最初のタッチの秒数に（なので、結果増える）
    - 使いどころは思い浮かばないがとりあえず用意しておいた。




### ジェスチャー

ジェスチャー系のパラメーターはフリック判定で使ったりするので、`.Update()` するまでは直前の値を保持し続ける。

`.Get***()` で Threshold を指定した場合は閾値を超えた分が返ってくる。
- 例： 閾値に 100（px）を指定して 123 ピクセル動いた場合、23 が返ってくる。

--

タッチしている指が２本の場合に `.SwipeVector` 他、１本指のジェスチャーを取ると `float.NaN` か `Vector2(float.NaN, float.NaN)` か `int.MinValue` が返ってくる。

なので、基本は `.FingerCount` で処理を分ける。




#### スワイプ


- `TouchRecognizer.SwipeVector`
    - スワイプのベクトル。
- `TouchRecognizer.SwipeDeltaVector`
    - スワイプの前フレームからの差分ベクトル（生値）
- `TouchRecognizer.GetSwipeVector(float distanceThreshold)`
- `TouchRecognizer.GetSwipeDeltaVector(float distanceThreshold)`
    - 指定した閾値（ピクセル）を超えた分のスワイプのベクトル。



#### フリック

フリックした後、カメラがスーーーっと止まる、をやろうとすると、ベクトルの減衰処理が必要だったりなので、機能を追加予定。


今時点でのフリック判定は、指数が減ったフレーム（`.IsFingerCountDecreased`）で、`.FingerCount` が望みの数の時に `.SwipeDeltaVector` 等の `.magnitude` が閾値を超えていたら `.SwipeVector` か `.SwipeDeltaVector` を使って良い感じにする、で出来る（ハズ




#### ピンチ（拡大・縮小）

- `TouchRecognizer.PinchLength`
    - ピンチの長さ（px）。縮めるジェスチャーだとマイナスの値。
- `TouchRecognizer.PinchDeltaLength`
    - 前フレームからの差分。
- `TouchRecognizer.GetPinchLength(float lengthThreshold)`
- `TouchRecognizer.GetPinchDeltaLength(float lengthThreshold)`
    - ピンチジェスチャーの長さ（w/閾値指定）


#### ピンチ（回転）

- `TouchRecognizer.PinchAngle`
    - ピンチで回した角度（反時計回り、度数でラジアンではない）
- `TouchRecognizer.PinchDeltaAngle`
    - デルタ。
- `TouchRecognizer.GetPinchAngle(float angleThresholdInDegrees)`
- `TouchRecognizer.GetPinchDeltaAngle(float angleThresholdInDegrees)`
    - 閾値指定。



#### ピンチ（スワイプ）

- `TouchRecognizer.PinchVector`
    - 2本指でのスワイプのベクトル。ピンチの拡縮や回転ではあまり反応しない（が全く無反応というわけではない）。
    - 2本指を同じ方向にスワイプした時のジェスチャを取る場合に使う。
- `TouchRecognizer.PinchDeltaVector`
    - Δ
- `TouchRecognizer.GetPinchVector(float distanceThreshold)`
- `TouchRecognizer.GetPinchDeltaVector(float distanceThreshold)`
    - 閾値。
