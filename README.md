# Eprice 論壇爬蟲程式

## 概述

此 Python 腳本用於從 [eprice.com.tw](https://www.eprice.com.tw/mobile/talk/4543/) 手機討論區擷取資料，包括貼文標題、連結、人氣、內容、發文時間等。依指定日期（最後回覆日期）過濾，並輸出 Pandas DataFrame。

**注意：** 網路爬蟲可能違反網站條款，請先檢查 robots.txt 與法律規定。僅限教育或個人使用。

## 功能

- 抓取論壇總頁數。
- 收集所有頁面的標題、連結、人氣、發文時間、最後回覆。
- 過濾指定日期的貼文。
- 擷取原始內容及最後回覆（限 100 字元）。
- 輸出欄位：title（含連結）、hot、Original、Original Date、Final、Final Date。

## 需求

- Python 3.x
- 套件：pandas, beautifulsoup4, requests

安裝：`pip install pandas beautifulsoup4 requests`

## 使用

```python
from eprice_scraper import geteprice  # 假設檔名為 eprice_scraper.py

df = geteprice(20190616)  # 抓取 2019-06-16 資料
print(df.head())
df.to_csv('forum_data.csv', index=False)
```

## 腳本分析

- `getpages(URL)`：取得總頁數。
- `get_mainpage(mainURL, totalpages)`：抓取所有頁面資料，跳過廣告。
- `deldatesbyrecentreply(df, date)`：依最後回覆日期過濾。
- `getlastcomment(URL, lastpage)`：抓最後回覆。
- `getarticle(df)`：補充內容。
- `geteprice(inputdate)`：主流程，輸出 DataFrame。

## 限制與改進

- 編碼固定 'big-5'，網站變更需調整。
- 無延遲，建議加 `time.sleep()` 防封鎖。
- 錯誤處理少，可加 try-except。
- 內容截斷 100 字，可調整。
- 未用函式如 `deldatesbyposttime` 可移除。

## 授權

MIT 授權，自由修改，負責使用。
