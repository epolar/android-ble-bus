# android-ble-bus


## 示例

#### 创建BleBus的监听器
```
    IBusListener listener = new IBusListener() {
        @Override
        public void deviceConnected(String address) {
            // TODO 设备连接成功
        }
    
        @Override
        public void deviceDisconnected(String address) {
            // TODO 蓝牙断开连接
        }
    
        @Override
        public void openBluetoothFailed() {
            // TODO 自动打开蓝牙失败了
        }
    
        @Override
        public void deviceRssiRead(String address, boolean success, int rssi) {
            // TODO 读取到Rssi信息
        }
    
        @Override
        public void listenOperateResult(BleService service, UUID characteristic, boolean success) {
            // TODO characteristic 监听结果
        }
    
        @Override
        public void writeOperateResult(BleService service, UUID characteristic, boolean success) {
            // TODO characteristic 写入结果
        }
    
        @Override
        public void readOperateResult(BleService service, UUID characteristic, boolean success) {
            // TODO  characteristic 读取结果
        }
    
        @Override
        public void dataReceived(BleService service, UUID characteristic, byte[] data) {
            // TODO  收到  characteristic 发来的Read/Notify/Indicate数据     
        }
    };
```

#### 创建bus实例
```
    ILogger logger = ...
    Ble bus = new BleBus(mCxt, listener, logger);

```

#### Write操作
```
    BleService service=new BleService("蓝牙地址", serviceUUID, characteristicUUID, valueToWrite, withResponseOrNot)
    bus.write(service);
```

#### Read操作
```
    BleService service=BleService("蓝牙地址", serviceUUID, characteristicUUID, OperateType.Read)
    bus.read(service)
```

#### Listen操作(Notify/Indicate)
```
    BleService service=BleService("蓝牙地址", serviceUUID, characteristicUUID, OperateType.Notify或者OperateType.Indicate)
    bus.listen(service)
```

#### ReadRSSi
```
    bus.readRssi("蓝牙地址")
```

#### 关闭连接
```
    bus.stop("蓝牙地址"...)
```




## Gradle
```
repositories {
	jcenter()
}
```
```
dependencies {
	compile 'li.xiangyang.android:blebus:0.4.4'
}
```
