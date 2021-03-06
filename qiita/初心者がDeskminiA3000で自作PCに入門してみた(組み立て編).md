# はじめに
- 久しぶりにバイト代がたくさん入ったので、以前から興味があったPC自作に初挑戦してみました。
- 使用したのは、Deskimini A3000という[小型ベアボーンキット](https://pcinformation.info/pcparts/barebone.html)です。ベアボーンキットとは、マザーボード・電源ユニット・PCケース等のパーツがセットになった商品で、難しい配線や組み立てなしでコンピュータの作成を体験することができます。
- 組み立てた後は、ubuntuをインストールしてwebサーバーとして運用してみる予定です。

# パーツ構成
- 以下が使用したパーツ構成です。
- なお、注文日はすべて2020.06.28です。


|  種類  |  パーツ  |  値段(税込み)  |
| ---- | ---- | ---- |
|  マザーボード&ケース&電源  | [ASRock DeskMini A300](https://www.amazon.co.jp/gp/product/B07MTRXVR7/ref=ppx_yo_dt_b_asin_title_o00_s00?ie=UTF8&psc=1) |  18,082円  |
|  CPU  |  [AMD CPU Athlon 200GE(3.2GHz 5Mキャッシュ 2コア4スレッド)](https://www.amazon.co.jp/gp/product/B07HJWVJDN/ref=ppx_yo_dt_b_asin_title_o01_s00?ie=UTF8&psc=1)  |  5995円  |
|  メモリ  |  [DDR4-2400 SODIMM 8GB x 1枚](https://www.amazon.co.jp/gp/product/B01LW6HBSM/ref=ppx_yo_dt_b_asin_title_o00_s00?ie=UTF8&psc=1)  |  4362円  |
|  SSD  |  [Crucial SSD 480GB 2.5インチ](https://www.amazon.co.jp/gp/product/B07H5B8734/ref=ppx_yo_dt_b_asin_title_o00_s00?ie=UTF8&psc=1)  |  6480円  |
|  合計  |    |  35175円  |

- DeskminiはUSB端子が少ない(前面1個、背面2個)ので、上記に加えて一つのUSBレシーバーでキーボードとマウスを同時に使える[Logicoolのキーボード](https://www.amazon.co.jp/gp/product/B01LW8E866/ref=ppx_yo_dt_b_asin_title_o00_s00?ie=UTF8&psc=1)を購入しました。

#### 机に広げるとこんな感じ
![8_IMG_3937.JPG](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/455240/3ff8d9e5-8ec8-4c39-3b95-06be23f67cfb.jpeg)

- CPUがたばこみたいですね。

# 組み立て

## 必要な道具
- ネジを外すのにプラスドライバーが必要です。

## Deskminiを開封するとこんな感じ
<img height="300" src="https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/455240/92ff2594-b295-ae15-7995-fb6523ffb151.jpeg">

## SSDを取り付ける
<img height="300" src="https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/455240/39e97492-9aeb-011a-9774-e5556bf79e0b.jpeg">

- マザーボードの背面にSSDを取り付けます。Deskminiに専用の接続コードが同封されているので、そちらを利用します。

## CPUを取り付ける
<img  height="300" src="https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/455240/9c6287a1-ed34-a22a-07a2-92fae19a1925.jpeg">

- CPUの向きに注意して取り付けます。静電気に注意してください。

## CPUファンとメモリを取り付ける
<img height="300" src="https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/455240/d595aa63-e35d-525d-26c3-ee3fe604154d.jpeg">

- CPUファンはDeskminiについてくるものと、CPUに同封されているものがありますが、今回はDeskminiについてくるものを取り付けました(多分同じものです)。
- グリスははじめからついているのでそのままくっつけて固定するだけです。
- メモリをつけるのに多少力がいるので壊さないように注意してください。

## 完成
<img height="300" src="https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/455240/b13a7560-3dab-c127-5c06-1d42b78b4c8f.jpeg">

- パーツを取り付けたら、ケースの中に戻して完成です！
- シールもついでに貼ってみました。かっこいいですね！


# BIOS確認
<img height="300" src="https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/455240/2d170177-fac5-bde2-e23b-3dfa9b4eb2e5.jpeg">

- CPUもメモリもきちんと認識されていますね！成功です！
- SSDやCPUファンも『Security』や『H/W Monitor』という項目で確認できます。

# 終わりに
- パーツが届いてから1時間もせずに組み立てることができました。
- CPUやメモリを生で見たのははじめてだったので楽しかったです。
- 普段コンピュータの構成等を意識する機会はなかなかないと思うので、勉強になりました。パーツを調べたり比較するだけでもいろんな知識がついて面白いです。
- 今回は簡易的でそこまでの性能ではないですが、今後はもっと高性能なマシンを作ってみたいです。
- OSのインストールやwebサーバーとしての運用方法については別記事にまとめることにします。

# 謝辞
- 使用するパーツや知識については[インターン先の先輩](https://ja.wikipedia.org/wiki/%E5%85%88%E8%BC%A9)に教えていただきました。本当にありがとうございます!

# 参考文献
- この[動画](https://www.youtube.com/watch?v=TDb-l-oN5-k)を見ながら組み立てました。
- [Ryzen 5 3400GとDeskMini A300で小型静音PCをつくる](https://qiita.com/ggaaii/items/21f70555a7fdab64a9fd)
- [ASrock deskmini 110とUbuntuで小型省電力サーバを作る【Ubuntu】](https://maywork.net/computer/deskmini-small-ubuntu-server/)
- [ASCIIの記事](https://ascii.jp/elem/000/001/902/1902338/2/)
