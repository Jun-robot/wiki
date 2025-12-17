---
feature: swarm/attachments/Pasted image 20251121001501.png
thumbnail: thumbnails/resized/84f73e45269bdc3cb86524fc453540f0_86cf658e.webp
---
#toio
## 先行事例
#### 複数台のサーバー
- ライゾマの事例 
    - [YOKOGAWA Brand Video “Connecting humanity and technology”]( https://rhizomatiks.com/work/yokogawa-brand-video/)
- 25個のtoioを9台のESP32で制御 
    - ESP32 1台で3台のtoio
    - ![](attachments/Pasted%20image%2020251121001501.png)
    - ![](attachments/Pasted%20image%2020251120234253.png)
    - これはWi-Fiも使わないことで、電波干渉の影響を最小限にしている
    - youさんから教えてもらった [リンク]( https://x.com/youtoy/status/1984052014557622550)
#### 単一サーバーについて
- 淳さんからのリプ [リンク](https://x.com/GEH00073/status/1987510570866880545)
    - Phone13 pythonista 10台
    - M1 MacAir 13台
    - M5Stack 9台
    - toio30台は持ってないらしい。
- M5でtoio制御
    - [toioをESP32(Arduino環境)で動かす | 新倉英生]( https://note.com/vhideo/n/nff5e2845beb1)
- 製品系
    -  [xMod]( https://shadan.xdiversity.org/xmod)
         - 落合陽一のxDiversityが作った
         - M5Stack Core2/CoreSがつく
         - 8800円
    - [ATOM Mate for toio™]( https://www.switch-science.com/products/8500?_pos=9&_sid=db1622d71&_ss=r)
        - ソニーとM5Stackが作った
        - ATOM Lite / ATOM Matrixがつく
        - バッテリーパックとtof
        - 5000円


#### 自分の検証
- RaspberryPi5 4GBの標準のbluettothで8台は動かせた
    - [自分のツイート]( https://x.com/jun_robot/status/1986875752302977258)

#### 懸念点
- bleセントラルの台数が増えることによる、自分のセントラル同士の干渉