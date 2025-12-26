# Eprice 論壇爬蟲程式

## 概述

從 [eprice.com.tw](https://www.eprice.com.tw/mobile/talk/4543/) 手機討論區擷取資料，包括貼文標題、連結、人氣、內容、發文時間等。依指定日期（最後回覆日期）過濾，並輸出 Pandas DataFrame。


## 功能

- 抓取論壇總頁數。
- 收集所有頁面的標題、連結、人氣、發文時間、最後回覆。
- 過濾指定日期的貼文。
- 擷取原始內容及最後回覆（限 100 字元）。
- 輸出欄位：title（含連結）、hot、Original、Original Date、Final、Final Date。

## 需求

- Python 3.x
- 套件：pandas, beautifulsoup4, requests

安裝：`pip install pandas beautifulsoup4`

