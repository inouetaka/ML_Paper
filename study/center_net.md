# Abstract(要旨)
Detection identifies objects as axis-aligned boxes in an image. Most successful object detectors enumerate a nearly exhaustive list of potential object locations and classify each.

```ディテクションでは画像内のオブジェクトに対して座標軸に平行なボックスとして識別します。最も成功したオブジェクト検出器は、潜在的なオブジェクトの場所のほぼ網羅的なリストを列挙し、それぞれを分類します。```

This is wasteful, inefficient, and requires additional post-processing. In this paper, we take a different approach.

```上記は無駄で効率が悪く追加の後処理が必要でした。この論文では私たちは違うアプローチを行いました。```

We model an object as a single point -- the center point of its bounding box. Our detector uses keypoint estimation to find center points and regresses to all other object properties, such as size, 3D location, orientation, and even pose.

```オブジェクトを単一の点、つまり境界ボックスの中心点としてモデル化します。私たちの検出器のキーポイントは中心点を推定し、サイズ、3D位置、方向、さらにはポーズなどの他のすべてのオブジェクトプロパティへの回帰を見つけます。```

Our center point based approach, CenterNet, is end-to-end differentiable, simpler, faster, and more accurate than corresponding bounding box based detectors.

```私たちの中心点ベースのアプローチであるCenterNetでは対応するバウンディングボックスベースの検出器よりもエンド2エンドで微分可能でシンプルかつ高速でより正確です。```

CenterNet achieves the best speed-accuracy trade-off on the MS COCO dataset, with 28.1% AP at 142 FPS, 37.4% AP at 52 FPS, and 45.1% AP with multi-scale testing at 1.4 FPS.

```CenterNetは最高の速度とトレードオフをMS COCOデータセットで達成します。平均精度は142FPSで28.1%、52FPSで37.4%、マルチスケールの場合は1.4FPSで平均精度は45.1%です。```

We use the same approach to estimate 3D bounding box in the KITTI benchmark and human pose on the COCO keypoint dataset. Our method performs compertitively with sophisticated multi-stage methods and runs in real-time.

```KITTIベンチマークの3D境界ボックスとCOCOキーポイントデータセットのヒトのポーズを推定するためにも同様の手法を用い、高度な多段階メソッドで競争力を発揮し、リアルタイムで実行します。```

## 単語帳
`identifies`:[他動]識別する   
`axis-aligned`:[-]座標軸に平行な   
`enumerate`:[他動]列挙する   
`exhaustive`:[形]徹底的に   
`inefficient`:[形]非効率な   
`requires`:[他動]~を必要とする   
`post-processing`:[名]後処理




# Introduction(はじめに)
Object detection powers many vision tasks like instance segmentation[7,21,32], pose estimation [3,15,39], tracking[24,27], and action recognition [5]. 

```オブジェクトディテクションはインスタンスのセグメンテーション[7,21,32]、姿勢推定[3,15,39]、追跡[24,27]、動作認識[5]のような多くの視覚タスクに力を発揮します。```


It has down-stream applications in surveillance [57], autonomous driving [53], and visual question answering [1].

```監視[57]や自動運転[53]、視覚的質問応答[1]などの側面も持っています。```

Current object detectors represent each object through an axis-aligned bounding box that tightly encompasses the object[18,19,33,43,46].

```現在のオブジェクト検出はオブジェクトをしっかりと包囲する軸に沿ったバウンディングボックスを介して各オブジェクトを表します[18,19,33,43,46]。```

They then reduce object detection to image classification of an extensive number of potential object bounding boxes.

```その後、多数のバウンディングボックスを減らしての潜在的オブジェクトを画像分類していきます。```

For each bounding box, the classifier determines if the image content is specific object or background.

```バウンディングボックス毎に画像が特定のコンテンツか背景かを判断していきます。```

One-stage detectors[33,43] slide a complex arrangement of possible bounding boxes, called anchors, over the image and classify them directly without specifying the vox content.

```単段検出器[33,43]はアンカーと呼ばれる可能性のある境界ボックスの複雑な配列を画像上にスライドさせ、それらをボックス内容を特定せずに直接分類する。```




