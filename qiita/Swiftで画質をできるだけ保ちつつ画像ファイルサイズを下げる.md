# はじめに
- iPhoneで写真を撮ると無駄に画像サイズが大きいですよね。
- iOSアプリで画像を扱いたいときにうざかったりします。
    - メモリを圧迫しますし、サーバーにアップロードする場合はサーバー代がかさみます。
- そこで、Swiftで画像ファイルサイズをなんとか下げたいと思ったのですが、ネット上にある方法だと画質がめちゃくちゃ悪くなってしまい困っていました。
- 色々試行錯誤して画質をできるだけ保ちつつ画像ファイルサイズを下げる方法を見つけたので共有します。

# 方法
ざっくり２つあります。
## 1 画像サイズをちっさくする
```swift
extension UIImage {

    func resize(targetSize: CGSize) -> UIImage {
        return UIGraphicsImageRenderer(size:targetSize).image { _ in
            self.draw(in: CGRect(origin: .zero, size: targetSize))
        }
    }

}
```

このメソッドを使ってください(sizeの部分は好きな値をいれてください)

```swift
var resizedPicture: UIImage = picture.resize(targetSize: CGSize(width: picture.size.width / 8, height: picture.size.height / 8))
```

## 2 jpegに変換する際のクオリティ(compressionQuality)を下げる

```swift
resizedPicture = resizedPicture.jpegData(compressionQuality: 0.25)
```

compressionQualityは0.0から1.0まで指定できますが、結構下げても画質が悪くならない(その割にファイルサイズはだいぶ下がる)のでおすすめです。

# 結果
iPhoneで撮影した1.3MBの画像が57KBになりました。
![IMG_4464.PNG](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/455240/0875e127-5c50-c578-1e2d-fd82256a845e.png)

## ネットにある方法との比較
### ネットにある方法( https://stackoverflow.com/questions/29137488/how-do-i-resize-the-uiimage-to-reduce-upload-image-size )で圧縮した画像
![IMG_4461.PNG](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/455240/08128049-d1df-8365-5940-67f6e40b1758.png)

画質に大きな差があることがわかります。しかも、画像ファイルサイズも前者は後者の半分以下に抑えられています。

# おわりに
- この方法を使えば画質を保ったまま画像ファイルサイズを下げることができます。
- ただ、なぜできるのか(正確にはネットでよくある方法ではなぜ画質がめちゃ悪くなるのか)、といった部分はよくわからないので今後調べてわかったら追記する予定です。

# 参考文献
- https://stackoverflow.com/questions/32612760/resize-image-without-losing-quality
- https://developer.apple.com/documentation/uikit/uiimage/1624115-jpegdata
- https://qiita.com/marty-suzuki/items/159b1c5d47fb00c11fda
