## 在本地跑AI功能
-   安裝ollama + openwebui + qwen2 1.5b模型在本地端對話，works!
-   安裝nvidia container toolkit啟動gtx1660s gpu加速，works!
-   安裝[stable-difussion-webui](https://github.com/AUTOMATIC1111/stable-diffusion-webui) 經gpu加速文生圖，works!
-   跑最近很紅的deepseek 1.5b完全跑在gpu上，速度很快，7b是92％跑在gpu，比較慢了，都可以跑，works!
-   vscode + continue + 本地端deepseek，嘗試跑AI助手，works!
-   安裝ComfyUI學習另一種工作流的文生圖，works!
-   嘗試生成影片，ongoing
-   用anythingllm做rag，輸入自己的履歷表txt檔可以檢索出資訊，有點google notebooklm的感覺。pdf似乎要找繁中友好的embedder，後來用qwen2.5:7b
-   openmanus裝了，只用CLI mode，每次都要跑完20輪，超級慢。qwen2.5-coder:7b用起來很怪，用14b過程正常一點但是最後結果沒產出，要再研究一下
