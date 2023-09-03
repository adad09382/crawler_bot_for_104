# crawler_bot_for_104

## 腳本功能

此腳本可從 104 網站上抓取職缺資料（如職缺標題、工作地點和經驗水平等）。並將結果以 Excel 文件格式輸出。

## 背景描述：

作者本人在使用 104 找工作時，發現 104 網頁的模糊搜索會搜到很多不相關職缺導致浪費時間，但使用嚴格條件搜索又怕有漏網之職缺。
想說如果寫一個腳本把所有模糊搜索返回的職缺資料寫進 excel 存下來的話，在具有最多相關資料下，再依照自己需求進行過濾，且可以達到記錄下該職缺的功能。

## 使用要求：

1.  確保電腦安裝了 Python 3.8+
2.  確保電腦安裝了 Chrome 瀏覽器
3.  確保已安裝以下 python 庫：

    - selenium
    - openpyxl
    - python-dotenv
    - fake_useragent

    安裝指令為：

        pip install selenium openpyxl python-dotenv fake_useragent

4.  確保您已下載 符合您 Chrome 版本的 ChromeDriver

## 使用步驟：

1.  clone 這一個儲存庫內容到你的本地

        git clone https://github.com/adad09382/crawler_bot_for_104.git

2.  在專案的根目錄中設置您的 .env 文件。它應該包含：

        CHROME_EXECUTABLE_PATH=您的chromedriver路徑

    **將您的 chromedriver 路徑替換為您的 chromedriver.exe 路徑**

## 使用方法：

1.  導航到專案目錄。

        cd 您的目錄路徑/crawler_bot_for_104

2.  完成欲爬取頁面的設定

    - 設定爬取欲爬取頁面 URL。(Must)
      目標頁面 URL 是只當 104 設定完查詢條件並搜索後跳轉的 URL，例如以下：
      在 104 設定完搜尋"職缺名"、"地點"、"經歷要求後"搜尋返回的 url 填入欲爬取頁面 URL。

      ![frontend_taipei](./readmeImg/frontend_taipei_job_search.png)

    - 設定最大滾動次數 ，預設為 45 次，可滾動獲取 15 pages 職缺，直到無法滾動自動加載。(Option)

3.  運行網頁爬蟲。

        python crawler_bot_for_104.py

- 開始運行後腳本將開始 Chrome 瀏覽器並導航到目標 URL (104 職缺網站)。
- 首先會透過滾動經過載入更多的職缺列表，當滾動結束後，開始判定網頁是否出現點擊 "載入更多" 按鈕載入職缺，完成並提取職缺的詳情。

- 提取的數據將保存在項目目錄的 jobs_list.xlsx 中。

- 完成後，瀏覽器將保持打開。在控制台按 Enter 以關閉瀏覽器。

## 運行效果

- 設定完欲爬取頁面後運行腳本，python 會開啟一個 chrome 瀏覽器，並在每幾秒內滾動畫面獲取更多的工作列表，直到最大滾動次數為止，之後進入判定網頁是否出現點擊 "載入更多" 按鈕載入職缺，最終完成並提取職缺的詳情建立 Excel。

![crawler_for_104_running](./readmeImg/crawler_for_104_running.gif)

- Excel 列表效果如下，包含 title、link、company、location、experience、description、salary 等數據

![crawler_for_104_result](./readmeImg/crawler_for_104_result.gif)

## 故障排除：

- 確保 chromedriver.exe 的版本與您的 Chrome 瀏覽器版本相匹配。
- 如果您在爬取過程中遇到任何問題，或者網站結構發生更改，則可能需要調整程式碼。

## 致謝：

感謝使用的 python 庫的創作者以及 104.com.tw 的團隊。

## 免責聲明

此代碼僅供教育目的使用。在爬取網站之前，確保您有權訪問數據，並且您遵守網站的 robots.txt 文件或服務條款。
如有任何疑慮請聯繫：d0372996@gmail.com
