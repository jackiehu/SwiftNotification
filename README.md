# SwiftNotification
简便通知操作
给NSObject扩展了一个属性：notifiCenter，继承自NSObject的类都可以很方便的使用它收发通知，不需要关心通知移除，deinit会自动移除
## 安装
```
支持ios9以上版本，swift4以上版本都支持
pod ‘Swift_Notification’
```## 使用

```
/// 发送通知
self.notifiCenter.postNotification(“123”, object: “aaaaaaa”, userInfo: [“key”:”fefe”])
```

```
/// 接收通知
self.notifiCenter.addNotification(“123”, callBack: { (noti) in
            print(“\(String(describing: noti.object)) — \(String(describing: noti.userInfo))”)
        })
```

api：
```
/// 移除所有通知
   func removeAllObserver()

/// 移除单个通知
    /// - Parameter name: 通知名称
   func removeObserverWithName(_ name : String?)

/// 移除多个通知
    /// - Parameter names: 通知名称数组
   func removeObserverWithNames(_ names : [String])

/// 注册添加通知
    /// - Parameters:
    ///   - name: 通知名称
    ///   - callBack: 通知执行的回调
   func addNotification(_ name : String, callBack : @escaping (Notification) -> Void)

/// 发送通知
    /// - Parameters:
    ///   - name: 通知名称
    ///   - object: 发送对象
    ///   - userInfo: 发送字典
   func postNotification(_ name : String, object: Any? = nil, userInfo : [String : Any]? = nil)
```
详细用法参见Demo **PushViewController**