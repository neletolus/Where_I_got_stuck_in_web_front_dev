# Matter.js メモ

## 衝突判定は取りたいが、物理演算はしたくない時
`isSensor`プロパティをMatter.bodyに付ける。  
その名の通り、物体をセンサーにしてくれるため、判定はあるが、実態はない状態となる。