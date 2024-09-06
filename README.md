# HK Supplement Market Analysis

This project involves a suite of Python scripts developed for web scraping data from Watson and HKTVmall, focusing on the analysis of the Hong Kong online supplement market. Designed for market analysts and data scientists, these tools automate the extraction of product details, customer reviews, and ratings. The collected data can be stored in a SQL database for comprehensive analysis, serving as a valuable resource for competitive intelligence, market research, and customer sentiment analysis.

# Features
- Automated Data Extraction Tool: Utilizes Selenium to systematically extract product details such as name, price, and descriptions from Watson and HKTVmall.
- Robust User Review Scraper: Extracts user reviews and ratings to offer comprehensive insights into customer perceptions and product quality.
- ETL Pipeline Setup: Establishes an ETL (Extract, Transform, Load) pipeline for seamless data processing.
- Seamless SQL Integration: Features a functionality to store extracted data in a SQL database, ensuring efficient and structured data storage.
- Flexible Crawling Configuration: Customizable script parameters empower users to tailor the crawling process to specific analytical or business requirements.


# Selenium

```
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.common.exceptions import NoSuchElementException
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
import time
import pandas as pd
from random import randint
from datetime import datetime

# 建立 Chrome 選項
chrome_options = webdriver.ChromeOptions()
chrome_options.add_argument("--disable-notifications")  # 禁用通知

# 建立 Chrome WebDriver 对象
driver = webdriver.Chrome(options=chrome_options)

url = "https://www.watsons.com.hk/zh-hk/%E5%81%A5%E5%BA%B7%E7%94%A2%E5%93%81/%E7%B6%9C%E5%90%88%E7%B6%AD%E4%BB%96%E5%91%BD/c/040313?pageSize=64&currentPage=0"

theurl = []
for i in range(2):
    # 去到你想要的网页
    driver.get(url)
    
    geturl = driver.find_elements(By.XPATH, "//h2/a[@class='ClickSearchResultEvent_Class gtmAlink']")
    for j in geturl:
        # 即时获取属性值并添加到 theurl 列表
        theurl.append(j.get_attribute('href'))
        
    time.sleep(55)
    
    # 将 URL 的 currentPage 参数递增
    current_page = int(url.split("currentPage=")[1]) + 1
    url = url.replace("currentPage=" + str(current_page - 1), "currentPage=" + str(current_page))
```
![Screenshot 2024-09-06 at 5 38 40 PM](https://github.com/user-attachments/assets/6b55fe1d-2c4c-4ef3-891b-c4e7028c72e5)



## Computing speed on different Hardware in Selenium
![Screenshot 2024-09-06 at 5 11 01 PM](https://github.com/user-attachments/assets/0441e48e-64aa-41a5-89be-ff3b7c052037)




# SQL database
### HKTVmall 
![Screenshot 2024-09-04 at 9 22 35 PM](https://github.com/user-attachments/assets/5a2f522a-ece2-4db8-93f8-0b166b9276d7) 

### HKWatsons 
![WhatsApp Image 2024-09-04 at 20 51 47](https://github.com/user-attachments/assets/7bb63ea1-1b7f-4823-bd9e-db5ed68e3709)

## Tableau
### Business Analysis
![Screenshot 2024-09-06 at 4 43 58 PM](https://github.com/user-attachments/assets/cf780a51-ecc4-4f4a-9ff8-d6b68ef2c389)


![Screenshot 2024-09-06 at 4 42 50 PM](https://github.com/user-attachments/assets/e912e304-2853-4048-9394-f591b9a91071)





