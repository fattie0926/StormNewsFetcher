# StormNewsFetcher

## 簡介
StormNewsFetcher 是一款運用 Python 和 BeautifulSoup 開發的新聞抓取工具，專門用於自動從[風傳媒](https://www.storm.mg/)網站抓取最新新聞。此工具通過解析網站的 HTML 結構來獲取新聞內容，並支援將內容透過 IFTTT 發送到 LINE 或其他平台。

## 功能
- **新聞抓取**：從風傳媒網站抓取最新新聞標題、內容及圖片。
- **字數限制**：提供選項限制新聞內容的字數，以適應不同平台的顯示需求。
- **自動發布**：透過 IFTTT Webhooks 功能，自動將新聞內容發送到 LINE 等平台。

## 原理
利用 `requests` 和 `BeautifulSoup` 對風傳媒網站進行 HTTP 請求和 HTML 內容解析，提取所需的新聞元素，如標題、內文和圖片連結。透過 IFTTT 的 Webhooks 服務，將新聞內容推送到指定的平台。

## 安裝
如果你在自己的電腦上執行的話，需安裝以下 Python 庫：
```
pip install requests
pip install beautifulsoup4
```

## 使用方式
1. **設定 IFTTT 的事件名稱和 Webhooks 密鑰**：
   - 確保您已在 IFTTT（[IFTTT.com](https://ifttt.com/)）註冊並創建帳號。
   - 前往 [My Applets](https://ifttt.com/my_applets) 並創建一個新的 applet。
   - `IF` 選擇 Webhooks 的 "Receive a web request" 作為觸發條件，並記下您設定的 `Event Name`。
   - `THEN` 選擇 " Send message" 作為欲執行的動作。
   - 在 LINE 的設定中，根據以下指示填寫 `Message` 和 `Photo URL` 兩個欄位：

     **Message 欄位:**
     ```
     <br>{{Value1}}<br>
     {{Value2}}<br>
     ```
     在此欄位中，`{{Value1}}` 和 `{{Value2}}` 將被替換為新聞標題和內容。

     **Photo URL 欄位:**
     ```
     {{Value3}}
     ```
     在此欄位中，`{{Value3}}` 將被替換為新聞中的圖片網址。
   
   - 保存並啟用 applet。

2. **運行提供的 Python 函數來抓取風傳媒的最新新聞**：
   - 在您的 Python 環境中運行 `fetch_content` 函數來獲取特定新聞的內容。
   - 或者使用 `fetch_latest_news_urls` 函數來獲取一系列最新新聞的 URL。
   - 兩者可以搭配使用，在筆記本的底部有範例程式碼可以直接運行。

3. **使用 `send_to_IFTTT` 函數將抓取的內容發送到您的 LINE 或其他支援 IFTTT 的平台**：
   - 確保您已將正確的 IFTTT 事件名稱和 Webhooks 密鑰填寫在代碼中。
   - 調用 `send_to_IFTTT` 函數以將新聞內容傳送至設定好的 IFTTT applet。

## 貢獻
歡迎對此項目做出貢獻。您可以通過提交 Pull Request 或開新的 Issue 來提出改善建議或報告問題。

## 致謝
特別感謝所有使用和支持此項目的朋友們。如有任何建議或問題，歡迎提出。

## 聯繫方式
若有任何疑問或建議，請透過以下方式聯繫我：
- 電子郵件：[fattie@fattie.io](mailto:fattie@fattie.io)

## 授權
本項目根據 MIT 授權條款發布。有關更多詳細信息，請參閱 [LICENSE](LICENSE) 文件。

---

Developer: [fattie0926](https://github.com/fattie0926)
