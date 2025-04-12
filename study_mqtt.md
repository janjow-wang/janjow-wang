# study mqtt

- 通常broker會放在外部，broker資源較強相對於mcu
```
     (Publisher)                      (Subscriber)
      [ MCU_1 ]                            [ MCU_2 ]
         │                                     ▲
         │ MQTT Publish                        │ MQTT Subscribe
         ▼                                     │
     ┌──────────┐        TCP/IP (通常是 WiFi 或 Ethernet)
     │  Broker  │  <------------------------------>
     │ (PC 上)  │        Mosquitto / EMQX 等
     └──────────┘
```
- 相比直連，好處是切斷耦合，分開處理，QoS，一對多的case是由broker處理
- pub/sub非固定，可以互換
- 有空實作看看 ongoing
