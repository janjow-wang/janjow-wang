## 待業期間做一些之前想做但沒做的事，持續加溫，避免冷卻
晚開始也是開始，keep walking
*   學習之前沒碰的東西
    *   玩了一下arduino，跑看看LED，蜂鳴器，控制外面的東西滿有趣的
    *   在職沒機會碰到，在YT的影片看uart，rs232，i2c，spi學習基礎概念
    *   買一個簡易USB LA可以觀察到arduino經UART打出來"a"的波形0x61 (01100001)，在LA的軟體上，works!
    *   又買了一個nodemcu-esp32s + ch340 usb_ttl線，可以跑example裡的wifiscan，com7裡面成功印出附近的SSID，works!
        *   原來arduiono ide裡面的serial monitor就能看到輸出不用另外接線用另一個com觀察，但是要把hp sure sense例外處理不然打不開serial monitor會一直報錯誤!
        *   安裝vscode + idf，works!
        *   idf build一個hello world，log可以看到更多訊息，改動freertos\app_startup.c可以在app_main之前印字出來，這裡應該就是交界點。
        *   這裡都會把freertos每次都重build(如果有改)跟之前不太一樣，前公司會預先作好幾種配置的kernel做成library，避免每個人用的不一樣， google了一下，esp32的freertos也可以做類似的設定，有機會再試。
        *   boot、ldr、heap、bin、gdb，有機會再試。
        *   crash：故意寫一個memset 0，crash後自動印出最後三層的trace，檔名行數函式名都有，連objdump都不用手動下，好人性!
        *   idf的qemu裝好後，可以在qemu裡面一步一步跑，下次來試gdb
    *   還買了一個mp3模組，ongoing
