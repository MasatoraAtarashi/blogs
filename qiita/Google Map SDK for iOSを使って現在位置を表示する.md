#  はじめに
GoogleMap SDK for iOSを利用して現在地をアプリ上に表示する方法については、[公式ドキュメント](https://developers.google.com/maps/documentation/ios-sdk/current-place-tutorial)を含めいくつか[記事](https://qiita.com/koogawa/items/adc2dd19015586bda39b)が存在しますが、どれもなぜかうまく動かなかったので、私の環境(Swift5・xcode11)で動いたコードを共有します。

なおコード全体は[こちら](https://github.com/MasatoraAtarashi/googlemap-sample-ios)で見れます。


#  SDKをインストール

```ruby:Podfile
source 'https://github.com/CocoaPods/Specs.git'
target 'YOUR_APPLICATION_TARGET_NAME_HERE' do
  pod 'GoogleMaps'
  pod 'GooglePlaces'
end
```

#  APIキーを取得

[こちら](https://developers.google.com/maps/documentation/ios-sdk/get-api-key#add_key)を参考にしてAPIキーを取得してください。そしてAppDelegateを以下のように編集します。

```swift:AppDelegate.swift
import GoogleMaps //これと

@UIApplicationMain
class AppDelegate: UIResponder, UIApplicationDelegate {

    func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
        // Override point for customization after application launch.

        GMSServices.provideAPIKey("YOUR API KEY") //これを追加

        return true
    }
```

#  info.plistを編集
以下を追加してください。

```xml:info.plist
<key>NSLocationWhenInUseUsageDescription</key>
	<string>現在位置の表示や、ルート案内を行うために位置情報を利用します。</string>
```

#  ViewControllerを編集

```swift:ViewController.swift
import UIKit
import GoogleMaps

class ViewController: UIViewController, CLLocationManagerDelegate {
    
    var locationManager = CLLocationManager()
    lazy var mapView = GMSMapView()

    override func viewDidLoad() {
        super.viewDidLoad()
        // Do any additional setup after loading the view.
        
        //初期値はApple本社
        let camera = GMSCameraPosition.camera(withLatitude: 37.3318, longitude: -122.0312, zoom: 17.0)
        mapView = GMSMapView.map(withFrame: CGRect(origin: .zero, size: view.bounds.size), camera: camera)
        mapView.settings.myLocationButton = true //右下のボタン追加する
        mapView.isMyLocationEnabled = true
        
        // User Location
        locationManager.delegate = self
        locationManager.requestWhenInUseAuthorization()
        locationManager.desiredAccuracy = kCLLocationAccuracyBest
        locationManager.startUpdatingLocation()
        
        self.view.addSubview(mapView)
        self.view.bringSubviewToFront(mapView)
    }
    
    //現在地が更新されたら呼び出される
    func locationManager(_ manager: CLLocationManager, didUpdateLocations locations: [CLLocation]) {
        let userLocation = locations.last
        
        let camera = GMSCameraPosition.camera(withLatitude: userLocation!.coordinate.latitude,
                                                          longitude: userLocation!.coordinate.latitude, zoom: 17.0)
        self.mapView.animate(to: camera)
        
        locationManager.stopUpdatingLocation()
    }

}
```

![スクリーンショット 2020-04-28 22.11.14.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/455240/ed5d8f11-a019-f205-1e30-1ddcfe301baf.png)
#  おわりに
サンプルによっては、mapViewを表示する際に

```swift:AppDelegate.swift
self.view = mapView
```

としているものがありますが(公式ドキュメント含め)、こうするとTabBarController等を利用しているときにアプリがクラッシュしますので、上記に書いたようにサブビューとして追加する方法を取った方が良いのではないかな、と思います。

#  参考
[公式ドキュメント](https://developers.google.com/maps/documentation/ios-sdk/start)
https://www.seemuapps.com/swift-google-maps-sdk-integration-with-current-location-and-markers

