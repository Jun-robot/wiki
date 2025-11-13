# nmcliの使い方

## 基本操作

### 接続プロファイルの確認
```bash
nmcli connection show
```

### ネットワークデバイスの状態確認
```bash
nmcli device status
```

### 見えてるWiFiのリスト
```bash
nmcli device wifi list
```

### 新しいWi-Fiの追加
```bash
sudo nmcli device wifi connect "SSIDを入れてね" password "パスワードを入れてね"
```
