
### 19.2

前文提到複利，本文要介紹的是複利的一個特例－－連續複利（Continuous Compounding），連續複利的概念是投資期數趨於無限大，而不同期之期的時間間隔無窮小，分分秒秒都在複利，也就是說剛剛生出的收益馬上就生出收益的收益，幾乎沒有時間間隔。如果單期簡單收益率（未考慮複利）是 $R$，該段期間有 $n$ 個複利結算週期，對應的 $T$ 期收益率為：

$$\big(1+\frac{R}{n}\big)^{nT}-1$$

根據連續複利的思想，當 $n\rightarrow\infty$ 時即得 $T$ 期連續複利的收益率：

$$\lim_{n\rightarror\infty}\big(1+\frac{R}{n}\big)^{nT}-1=e^{RT}-1$$

在連續複利下，期初投資 $A_0$ 元持有到 $T$ 期結束，資產會變成 $A_0e^{RT}$元。現在假設單期簡單收益率是 $R_t$，透過連續複利產生與 $R_t$ 相同收益的單期複利收益率叫做連續複利收益率（Continuous Compounded Rate of Return），該收益率（記號為 $r_t$）應該滿足：

$$1+R_t=e^{r_t}，$$

即

$$r_t=\ln(1+R_t)$$

如果 $1+R_t$ 是用資產的期初價格 $P_{t-1}$ 及期末價格 $P_{t}$ 求得，則

$$r_t=\ln(\frac{P_t}{P_{t-1}})=\ln P_t-\ln P_{t-1}$$

即資產的單期連續複利收益率等於資產期初期末價格的自然對數之差。

以台積電股票為例，2015 年 1 月 6 日的收盤價為 124.50 元，1 月 7 日的收盤價為 124.97 元，透過計算，得知 1 月 7 日的單期簡單收益率：

$$\frac{124.97-124.50}{124.50}=0.3775\%$$

對應的單期連續複利收益率為：

$$r_6=\ln(124.97)-\ln(124.50)\approx0.3768\%$$

若用 Python 來計算單期連續複利收益率，我們可以根據公式自己寫程式碼實作：

import numpy as np
comporet=np.log(close/lagclose)
comporet.name='comporet'
comporet.head()

我們也可以呼叫 ffn 套件中計算複利收益率的函數 to_log_returns()，具體方法為：

`to_log_returns(prices)`

其中 prices 是我們要計算收益率的股票價格。仍以台積電企業 2015 年的股票資料為例進行說明。

ffnComporet=ffn.to_log_returns(close)
ffnComporet.head()