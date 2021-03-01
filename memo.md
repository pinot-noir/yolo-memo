Windowsでやる場合

1.cuda/cudnnを入れる

https://rupic.hatenablog.com/entry/2020/03/24/021455

2.Visual Studioでビルド

https://qiita.com/n-yamanaka/items/b5c45a961560340b300

2-1.Visual Studio 2019を使う場合、このように選択する
![image](https://user-images.githubusercontent.com/58208642/109466633-60fc2400-7aad-11eb-8973-f8e6332da335.png)

build\darknet\darknet.slnをVisual Studioで開く

2-2.プロジェクトを右クリックし、プロパティを開く。
「C/C++」→「全般」→「追加のインクルードディレクトリ」で以下を追加。
※既存は消さない。またパスが間違っていたら修正
```
C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v9.2\bin
C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v9.2\include
C:¥opencv\build\x64\vc14\include
```

2-3.「リンカー」→「全般」→「追加のライブラリディレクトリ」で以下を追加。

※既存は消さない。またパスが間違っていたら修正
```
C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v9.2\lib
C:¥opencv\build\build\x64\vc14\lib
```

2-4.「CUDA C/C++」→「Device」→「Code Generation」を書き換える

`compute_80,sm_80`

となっているはずなので、自分が利用しているGPUのアーキテクチャの値に変更。

このサイトを参考に自分のGPUの値を確認：https://arnon.dk/matching-sm-architectures-arch-and-gencode-for-various-nvidia-cards/

2-5.ビルド

プロジェクトを右クリックしてビルド、正常にビルドされればx64ディレクトリにdarknet.exeが生成される。
