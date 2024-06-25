# Three.js

## アニメーションを最後のフレームで止めたい時。
アニメーションの`clampWhenFinished`をtrueにする。

```javascript
model.setAttribute('animation-mixer', { clip: 'Animation', loop: 'once', clampWhenFinished: true })
```

## アニメーションの終了を受け取れない。
原因はThree.jsのLoopタイプの指定ミスが多い。  

Loopタイプは下記の三つ
- once
  - 一度だけアニメーション実行
- repeat
  - repetitionsに指定した数繰り返す
- pingpong
  - アニメーションループごとに再生、逆再生を繰り返す

終了させたいならrepetitionsを指定するか、onceにすれば良い。



