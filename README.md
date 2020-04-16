# 2020_Taiwan_PTT_WHO

分析 2020 年 1 月 1 日至 4 月 15 日的 PTT 八卦版所有與 WHO 有關文章及留言，判斷是否存在歧視性言論。

---

1. [ 前言 ](#前言)
2. [ 資料集 ](#資料集)
3. [ 與 WHO 有關的文章 ](#WHO)
4. [ 詞頻分析 ](#詞頻分析)
5. [ 歧視性言論 ](#歧視性言論)
   - [ 發表歧視性言論的鄉民 ](#發表歧視性言論的鄉民)
   - [ 含有歧視性言論的發文 ](#含有歧視性言論的發文)
   - [ 含有歧視性言論的留言 ](#含有歧視性言論的留言)

---

<a name="前言"></a>
## 前言

昨天（14）看到兩篇文章，心生好奇，遂復現同樣的分析。

[文章 1：中评社｜于强：从大数据看台湾网民如何攻击谭德塞](https://mp.weixin.qq.com/s?__biz=MzA3MTAyMzAxMg==&mid=2650529205&idx=2&sn=809777ddf6ece63eb374e0a2a554618a&chksm=873c9d7eb04b14684254f7ed3392ae4f3b1a246c91b7c00616f093917d7b9113b6adf3fd078f&mpshare=1&scene=1&srcid=0414ujyrmvkOXSnnFdh1MqAY&sharer_sharetime=1586856059175&sharer_shareid=4417ffdfb25ca55d018f7a9ed769a267#rd)

[文章 2：天下雜誌｜學者3數據，揪台灣人都怎麼「罵」譚德塞](https://www.cw.com.tw/article/article.action?id=5099796)

<a name="資料集"></a>
## 資料集

PTT 八卦版 27900 頁～39199 頁（1/1～4/15）共 219461 篇文章。

> 使用 [GitHub｜jwlin/ptt-web-crawler](https://github.com/jwlin/ptt-web-crawler) 爬取 PTT 文章

<a name="WHO"></a>
## 與 WHO 有關的文章

參考前言提到的兩篇文章，舉凡文章中（不包括留言）出現「WHO、世界衛生組織、世衛組織、譚德塞」任一關鍵字，即判定為**與 WHO 有關**。

得到的結果如下圖所示，共 5318 篇文章與 WHO 有關。大約在 1/15 後才有明顯的聲量，並在 4/9 和 4/11 達到最高峰，佔當天八卦版的 12% 左右。可能分別與[譚德塞指台灣人身攻擊3個月](https://www.cna.com.tw/news/firstnews/202004095012.aspx)和[募資「紐時」反擊譚德塞](https://tw.news.yahoo.com/募資-紐時-反擊譚德塞-18小時封關破千萬-052153037.html)等事件對應。

> 此處的事件對應結果並沒有通過分析文本得到，僅僅與當天發生的大事做連結而已。

![](https://i.imgur.com/BK2H2ci.png)

> 截至止 4/15 中午左右。
 
> 3/7 和 3/13 檔案讀取發生錯誤，但不影響結果。
 
<a name="詞頻分析"></a>
## 詞頻分析

使用 [fxsjy/jieba](https://github.com/fxsjy/jieba) 分詞，並加強特定詞彙的關聯性。

```python
jieba.suggest_freq('世界衛生組織', True)
jieba.suggest_freq('世衛組織', True)
jieba.suggest_freq('譚德塞', True)
```
詞頻統計時忽略以下詞彙

```python
ignore = {'的','在','是','有','了','也','都','人','對','說','就','不','我','你',
          '日','1','於','月','被','和','沒','來','但','要','會','我們','表示',
          '為','與','到','年','啊','嗎','好','去','啦','跟','吧','真的','自己',
          '就是','不是','很','不要','可以','又','才','喔','他','什麼','2','='
          '或','3','4','後','上'}
```
得到的結果按月份展示如下，並以文章和文章底下的留言分別統計。

### 1 月

1 月份與 WHO 相關文章共 802 篇，613179 字。

![](https://i.imgur.com/JNRWAPI.png)

1 月份與 WHO 相關文章底下的留言共 74522 則，763185 字。

![](https://i.imgur.com/stzXwWf.png)

### 2 月

2 月份與 WHO 相關文章共 1477 篇，1049442 字。

![](https://i.imgur.com/oiZchPU.png)

2 月份與 WHO 相關文章底下的留言共 138790 則，1435738 字。

![](https://i.imgur.com/GJ19XIf.png)

### 3 月

3 月份與 WHO 相關文章共 1241 篇，1068733 字。

![](https://i.imgur.com/HH393u3.png)

3 月份與 WHO 相關文章底下的留言共 112241 則，1193964 字。

![](https://i.imgur.com/ELEE7Ln.png)

### 4 月

4 月份與 WHO 相關文章共 1087 篇，807046 字。

![](https://i.imgur.com/dinvLGd.png)

4 月份與 WHO 相關文章底下的留言共 107080 則，1318357 字。

![](https://i.imgur.com/NqSgA0R.png)

<a name="歧視性言論"></a>
## 歧視性言論

參考前言提到的兩篇文章，此處僅定義「尼哥」為歧視性言論，統計各月份的文章和留言提到「尼哥」的次數。

<img src="https://i.imgur.com/QLz8xdM.png" width="600" />

<img src="https://i.imgur.com/mSU6gqD.png" width="600" />

歧視性言論總計 2952 次，與 [文章 1](https://mp.weixin.qq.com/s?__biz=MzA3MTAyMzAxMg==&mid=2650529205&idx=2&sn=809777ddf6ece63eb374e0a2a554618a&chksm=873c9d7eb04b14684254f7ed3392ae4f3b1a246c91b7c00616f093917d7b9113b6adf3fd078f&mpshare=1&scene=1&srcid=0414ujyrmvkOXSnnFdh1MqAY&sharer_sharetime=1586856059175&sharer_shareid=4417ffdfb25ca55d018f7a9ed769a267#rd) 提到的 4031 略有差異；考慮總共 432633 則留言中有 2874 則涉及歧視性言論，佔比約千分之七，與 [文章 2](https://www.cw.com.tw/article/article.action?id=5099796) 提到的不及千分之五接近。

<a name="發表歧視性言論的鄉民"></a>
### 發表歧視性言論的鄉民

無論是發文或是留言，可以排除由特定幾位鄉民多次發表歧視性言論的可能性，從 `id` 和 `author` 上看來，大多是來自不同人。

<img src="https://i.imgur.com/R3O660H.png" width="400" />

<img src="https://i.imgur.com/iEgDQao.png" width="400" />

<a name="含有歧視性言論的發文"></a>
### 含有歧視性言論的發文

[0127 [問卦] 落後國家尼哥當WHO高官？](https://www.ptt.cc/bbs/Gossiping/M.1580099155.A.D39.html)

[0129 [問卦] 具體來說加入WHO有啥好處?](https://www.ptt.cc/bbs/Gossiping/M.1580239272.A.EF7.html)

[0130 Re: [問卦] 為什麼忽然一堆國家 希望我們加入WHO?](https://www.ptt.cc/bbs/Gossiping/M.1580394751.A.515.html)

[0130 [問卦] WHO老早是支那的形狀了？](https://www.ptt.cc/bbs/Gossiping/M.1580348571.A.AFF.html)

[0130 [問卦] 照世衛WHO的說法 中國根本沒必要捐口罩ㄅ](https://www.ptt.cc/bbs/Gossiping/M.1580392368.A.3E9.html)

[0130 [問卦] 黑種人去中共國念書是不是獎勵優渥阿?!](https://www.ptt.cc/bbs/Gossiping/M.1580383334.A.B9A.html)

[0131 [問卦] WHO 是疫情擴散的最大幫兇嗎？](https://www.ptt.cc/bbs/Gossiping/M.1580478654.A.94F.html)

[0203 Re: [新聞] 世衛秘書長再籲各國政府：無須為防疫](https://www.ptt.cc/bbs/Gossiping/M.1580733828.A.2C8.html)

[0204 Re: [新聞] WHO執委會登場 中國誤導國際對台認知](https://www.ptt.cc/bbs/Gossiping/M.1580746047.A.92F.html)

[0205 Re: [新聞] WHO灌水 台灣武漢肺炎確診竟變13例](https://www.ptt.cc/bbs/Gossiping/M.1580913574.A.FA9.html)

[0207 Re: [新聞] 譚德塞家鄉航空續航中國 將非洲暴露危險](https://www.ptt.cc/bbs/Gossiping/M.1581060669.A.E1A.html)

[0207 [新聞] 譚德塞家鄉航空續航中國 將非洲暴露危險](https://www.ptt.cc/bbs/Gossiping/M.1581059553.A.E5C.html)

[0210 [新聞] 奈及利亞爆發拉薩熱 造成29人死亡](https://www.ptt.cc/bbs/Gossiping/M.1581350089.A.120.html)

[0214 Re: [新聞]  川普新預算刪「全球衛生基金」30億…WHO](https://www.ptt.cc/bbs/Gossiping/M.1581670124.A.372.html)

[0215 [問卦] WHO為什麼敢拿美國錢幫中國講話?](https://www.ptt.cc/bbs/Gossiping/M.1581782367.A.6BB.html)

[0221 Re: [問卦] 為什麼台韓馬能成功，非洲不能?](https://www.ptt.cc/bbs/Gossiping/M.1582227680.A.202.html)

[0222 Re: [新聞] 武漢肺炎蔓延 譚德塞坦承：遏疫情之窗](https://www.ptt.cc/bbs/Gossiping/M.1582337546.A.51E.html)

[0227 [新聞] 陳建仁：台若參加WHO 可預防新冠肺炎爆發](https://www.ptt.cc/bbs/Gossiping/M.1582784320.A.A2D.html)

[0228 [問卦] 台灣沒有參加WHO是不是反而逃過一劫？](https://www.ptt.cc/bbs/Gossiping/M.1582859737.A.A9D.html)

[0228 [問卦] 為什麼要加入WHO？](https://www.ptt.cc/bbs/Gossiping/M.1582854797.A.AE4.html)

[0229 Re: [問卦] 外國人真的會相信WHO的話嗎？](https://www.ptt.cc/bbs/Gossiping/M.1582910574.A.988.html)

[0229 [問卦] 外國人真的會相信WHO的話嗎？](https://www.ptt.cc/bbs/Gossiping/M.1582908842.A.0FB.html)

[0229 [新聞] 世衛組織：新冠肺炎疫情風險級別上調至「非常高」](https://www.ptt.cc/bbs/Gossiping/M.1582908861.A.C9F.html)

[0303 [問卦] 現實世界有沒有九頭蛇組織?](https://www.ptt.cc/bbs/Gossiping/M.1583242916.A.B38.html)

[0304 [問卦] 明年CHO會不會制定武漢肺炎紀念日](https://www.ptt.cc/bbs/Gossiping/M.1583336736.A.E4F.html)

[0304 [爆卦] 5ch 對中國外交部不爽武漢肺炎稱呼的看法](https://www.ptt.cc/bbs/Gossiping/M.1583330348.A.784.html)

[0307 [問卦] 台灣CDC跟美國CDC組團應該是世界最強吧?](https://www.ptt.cc/bbs/Gossiping/M.1583579492.A.C13.html)

[0311 Re: [問卦] 誰會是2020年的終極幹話王？](https://www.ptt.cc/bbs/Gossiping/M.1583897139.A.62C.html)

[0311 [問卦] 譚德賽跟習近平誰是1誰是0](https://www.ptt.cc/bbs/Gossiping/M.1583861616.A.F19.html)

[0312 [問卦] 那個尼哥塞會被國際法庭審判嗎？](https://www.ptt.cc/bbs/Gossiping/M.1583978673.A.6AE.html)

[0313 [問卦] 中國恐成最大贏家](https://www.ptt.cc/bbs/Gossiping/M.1584076029.A.1BA.html)

[0314 [問卦] WHO會被秋後算帳嗎？](https://www.ptt.cc/bbs/Gossiping/M.1584163736.A.545.html)

[0315 [新聞] 歐洲是病毒中心，每日確診數「超過中國爆](https://www.ptt.cc/bbs/Gossiping/M.1584230174.A.270.html)

[0316 [問卦] 垃圾黑人譚德塞 死後會下地獄嗎?](https://www.ptt.cc/bbs/Gossiping/M.1584352008.A.CE8.html)

[0317 Re: [問卦] 如果譚德賽確診會發生什麼事](https://www.ptt.cc/bbs/Gossiping/M.1584455832.A.104.html)

[0317 Re: [問卦] 所以二級三級差在哪?](https://www.ptt.cc/bbs/Gossiping/M.1584420542.A.A30.html)

[0317 Re: [問卦] 所以旅遊二級三級差在哪?](https://www.ptt.cc/bbs/Gossiping/M.1584421148.A.491.html)

[0317 [問卦] 如果譚德賽確診會發生什麼事](https://www.ptt.cc/bbs/Gossiping/M.1584450626.A.2B9.html)

[0317 [問卦] 所以二級三級差在哪?](https://www.ptt.cc/bbs/Gossiping/M.1584420162.A.FF7.html)

[0318 [問卦] 所以說WHO要幹嘛](https://www.ptt.cc/bbs/Gossiping/M.1584501448.A.E59.html)

[0319 Re: [問卦] 中國怎麼還不制裁美國？](https://www.ptt.cc/bbs/Gossiping/M.1584624809.A.312.html)

[0320 [問卦] 這波疫情結束後支那會被清算嗎？](https://www.ptt.cc/bbs/Gossiping/M.1584635865.A.6BE.html)

[0325 [問卦] 第三世界尼哥為何會主導世界衛生?](https://www.ptt.cc/bbs/Gossiping/M.1585109868.A.7EC.html)

[0327 [問卦] 所以WHO的作用是?](https://www.ptt.cc/bbs/Gossiping/M.1585314861.A.B2D.html)

[0327 [問卦] 歐美其實根本不在乎防疫吧？](https://www.ptt.cc/bbs/Gossiping/M.1585246158.A.DB8.html)

[0331 [政治] 住台灣很安全！20外國人拍片讚爆台防疫](https://www.ptt.cc/bbs/Gossiping/M.1585615521.A.731.html)

[0404 Re: [新聞] 世衛發現口罩有保護作用 或籲民眾戴口罩](https://www.ptt.cc/bbs/Gossiping/M.1586011030.A.D05.html)

[0408 Re: [新聞] 俄羅斯大爆發！24小時新增1154例確診](https://www.ptt.cc/bbs/Gossiping/M.1586306329.A.3EC.html)

[0408 [政治] 歐美會反思政治正確的假道學嗎？](https://www.ptt.cc/bbs/Gossiping/M.1586323776.A.DCA.html)

[0409 Re: [問卦] 老實說  譚得塞罵台灣人也沒罵錯吧？](https://www.ptt.cc/bbs/Gossiping/M.1586402270.A.BC7.html)

[0409 Re: [政治] 快訊／譚德塞痛罵台灣3分鐘　外交部700](https://www.ptt.cc/bbs/Gossiping/M.1586397106.A.87F.html)

[0409 Re: [政治] 譚德塞稱遭台灣網軍攻擊 陳時中:自有公斷](https://www.ptt.cc/bbs/Gossiping/M.1586374823.A.F83.html)

[0409 Re: [新聞] 澳媒問「誰阻止發布全球公衛緊急事件」](https://www.ptt.cc/bbs/Gossiping/M.1586406943.A.BF7.html)

[0409 Re: [爆卦] 5ch對譚德塞炮轟台灣的反應](https://www.ptt.cc/bbs/Gossiping/M.1586435090.A.62E.html)

[0409 Re: [爆卦] 罵譚德賽尼哥的人找到了](https://www.ptt.cc/bbs/Gossiping/M.1586429670.A.D4F.html)

[0409 [問卦] 台灣經過這次會學乖嗎](https://www.ptt.cc/bbs/Gossiping/M.1586411187.A.632.html)

[0409 [問卦] 有堵藍在 還要求WHO幫台灣???](https://www.ptt.cc/bbs/Gossiping/M.1586418968.A.929.html)

[0409 [問卦] 為啥譚得塞能當上WHO總幹事？](https://www.ptt.cc/bbs/Gossiping/M.1586394482.A.6FF.html)

[0409 [爆卦] 譚德賽在WHO記者會罵台灣](https://www.ptt.cc/bbs/Gossiping/M.1586370402.A.2F4.html)

[0410 Re: [新聞] 台灣人攻擊譚德塞？調查局：查無辱罵確切](https://www.ptt.cc/bbs/Gossiping/M.1586493898.A.271.html)

[0410 Re: [爆卦] 大陸網友可翻譯告知歐美 台灣辱罵世衛整](https://www.ptt.cc/bbs/Gossiping/M.1586462708.A.D12.html)

[0410 [問卦] 摩根費里曼願意演譚德塞嗎？](https://www.ptt.cc/bbs/Gossiping/M.1586480524.A.AA7.html)

[0410 [政治] 台灣政府回應世衛的模式很失敗](https://www.ptt.cc/bbs/Gossiping/M.1586449207.A.8ED.html)

[0410 [新聞]鄉民逞口舌之快 疫外傷害台灣](https://www.ptt.cc/bbs/Gossiping/M.1586476154.A.299.html)

[0411 Re: [問卦] 15320人能代表台灣的正當性？](https://www.ptt.cc/bbs/Gossiping/M.1586580776.A.1E0.html)

[0411 Re: [問卦] 叫黑人那裡錯了？](https://www.ptt.cc/bbs/Gossiping/M.1586577384.A.F7F.html)

[0411 Re: [問卦] 合PTT眾人之力寫封公開信會是啥樣子](https://www.ptt.cc/bbs/Gossiping/M.1586590558.A.7B3.html)

[0412 Re: [政治] 調查局：中國網軍假冒台灣網友攻訐譚德塞](https://www.ptt.cc/bbs/Gossiping/M.1586693524.A.E08.html)

[0412 Re: [爆卦] 外交部勸告鄉民珍惜台新關係](https://www.ptt.cc/bbs/Gossiping/M.1586691987.A.D3B.html)

[0412 [爆卦] 5ch評"陳時中公佈WHO電郵"](https://www.ptt.cc/bbs/Gossiping/M.1586658431.A.EB2.html)

[0413 Re: [問卦] 其實大部份國家都不喜歡台灣](https://www.ptt.cc/bbs/Gossiping/M.1586726231.A.534.html)

[0413 Re: [政治] 台灣真的沒攻擊譚德塞嗎？新加坡媒體刊文](https://www.ptt.cc/bbs/Gossiping/M.1586761981.A.B32.html)

[0413 Re: [政治] 藍委要法務部公布只是堵藍IP 證明歧視言](https://www.ptt.cc/bbs/Gossiping/M.1586746803.A.66E.html)

[0413 [問卦] 不要罵譚德塞黑鬼尼哥惹，好嗎](https://www.ptt.cc/bbs/Gossiping/M.1586724344.A.8EC.html)

[0413 [問卦] 你越黑，我越挺？](https://www.ptt.cc/bbs/Gossiping/M.1586739029.A.F5F.html)

[0413 [問卦] 其實大部份國家都不喜歡台灣](https://www.ptt.cc/bbs/Gossiping/M.1586709276.A.1F1.html)

[0413 [政治] 藍委要法務部公布只是堵藍IP 證明歧視言](https://www.ptt.cc/bbs/Gossiping/M.1586745891.A.1F7.html)

[0414 Re: [新聞] 快訊／阿滴募資《紐時》廣告今晚刊登　](https://www.ptt.cc/bbs/Gossiping/M.1586877587.A.4DE.html)

<a name="含有歧視性言論的留言"></a>
### 含有歧視性言論的留言

[0120 peter105096：整個聯合國都中共的形狀啊 尼哥國收](https://www.ptt.cc/bbs/Gossiping/M.1579532748.A.45D.html)

[0122 grandwar：一堆尼哥取暖大會，主席最近還在推特發](https://www.ptt.cc/bbs/Gossiping/M.1579693219.A.119.html)

[0123 amaranth5566：尼哥主持的會議](https://www.ptt.cc/bbs/Gossiping/M.1579767604.A.7D2.html)

[0123 kangta0819：裡面都是「要錢要資源的尼哥+支那賤畜](https://www.ptt.cc/bbs/Gossiping/M.1579792623.A.ABF.html)

[0123 s866217：一群垃圾尼哥+支那賤畜](https://www.ptt.cc/bbs/Gossiping/M.1579792538.A.A0E.html)

[0124 MK47：中國和尼哥組織](https://www.ptt.cc/bbs/Gossiping/M.1579869092.A.986.html)

[0124 chiguang：瘟疫公司的作弊模式要加上WHO是尼哥](https://www.ptt.cc/bbs/Gossiping/M.1579821608.A.956.html)

[0124 felixr0123：哈哈垃圾尼哥](https://www.ptt.cc/bbs/Gossiping/M.1579856228.A.045.html)

[0124 goldflower：垃圾尼哥組織 太窮被中國人當作乞丐](https://www.ptt.cc/bbs/Gossiping/M.1579856498.A.CA3.html)

[0124 kivan00：中文叫做中國與快樂的尼哥小夥伴](https://www.ptt.cc/bbs/Gossiping/M.1579868581.A.508.html)

[0124 kobe9527：尼哥組織](https://www.ptt.cc/bbs/Gossiping/M.1579832515.A.673.html)

[0124 roy2142：一年大概又不知道要花多少錢去養這些尼哥](https://www.ptt.cc/bbs/Gossiping/M.1579805027.A.DC3.html)

[0124 widec：WHO主席就只是一隻支那控制下的傀儡尼哥](https://www.ptt.cc/bbs/Gossiping/M.1579849149.A.998.html)

[0125 MK47：本來就是中國和尼哥快樂團 能負什麼責任？](https://www.ptt.cc/bbs/Gossiping/M.1579961476.A.AA9.html)

[0125 ToTo0306：織跟那個尼哥發言人真的是看了一肚子火](https://www.ptt.cc/bbs/Gossiping/M.1579885696.A.2BF.html)

[0125 a176893：是誰讓尼哥加入WHO的](https://www.ptt.cc/bbs/Gossiping/M.1579953814.A.A02.html)

[0125 a176893：誰讓尼哥進WHO的](https://www.ptt.cc/bbs/Gossiping/M.1579930792.A.93E.html)

[0125 a7983115：尼哥是用撥接的嗎？](https://www.ptt.cc/bbs/Gossiping/M.1579927099.A.F5E.html)

[0125 felixr0123：這垃圾尼哥 我看罪孽很重了](https://www.ptt.cc/bbs/Gossiping/M.1579888595.A.4C6.html)

[0127 OVERDRUNK：這任剛好又是跟中共麻吉的非洲尼哥](https://www.ptt.cc/bbs/Gossiping/M.1580099155.A.D39.html)

[0127 a3221715：垃圾尼哥](https://www.ptt.cc/bbs/Gossiping/M.1580093127.A.A24.html)

[0127 ice76824：尼哥還是回去種棉花吧](https://www.ptt.cc/bbs/Gossiping/M.1580108718.A.764.html)

[0128 BigLarry：死非洲尼哥 各國都已決定拒絕中客才改](https://www.ptt.cc/bbs/Gossiping/M.1580194616.A.7AD.html)

[0128 HAHAHUNG：尼哥還在講幹話](https://www.ptt.cc/bbs/Gossiping/M.1580225843.A.65E.html)

[0128 a3221715：非緊急還叫尼哥來開會喔](https://www.ptt.cc/bbs/Gossiping/M.1580220340.A.269.html)

[0128 c871111116：尼哥+支那 真是經典廢物組合](https://www.ptt.cc/bbs/Gossiping/M.1580175973.A.BB9.html)

[0128 cocabell：ChinaHO尼哥幹事聽訓中，小李子嗎？](https://www.ptt.cc/bbs/Gossiping/M.1580199844.A.963.html)

[0128 dlevel：中國人當秘書長，還有這個尼哥](https://www.ptt.cc/bbs/Gossiping/M.1580207466.A.79E.html)

[0128 goldflower：智障尼哥](https://www.ptt.cc/bbs/Gossiping/M.1580210073.A.896.html)

[0128 grandwar：尼哥](https://www.ptt.cc/bbs/Gossiping/M.1580192105.A.25F.html)

[0128 gy3310：尼哥專給支那幹](https://www.ptt.cc/bbs/Gossiping/M.1580203406.A.2C7.html)

[0128 slimfat0202：尼哥，去死](https://www.ptt.cc/bbs/Gossiping/M.1580192561.A.511.html)

[0128 syterol：尼哥真的沒用](https://www.ptt.cc/bbs/Gossiping/M.1580174755.A.52A.html)

[0128 xxxg00w0：尼哥你準備被中二川玩死吧..前面這樣耍](https://www.ptt.cc/bbs/Gossiping/M.1580215161.A.074.html)

[0129 grandwar：我現在覺得用尼哥形容他還太好了，尼哥](https://www.ptt.cc/bbs/Gossiping/M.1580278116.A.837.html)

[0129 newstarisme：尼哥正在被餵食中沒空](https://www.ptt.cc/bbs/Gossiping/M.1580254495.A.21F.html)

[0129 oldlu2002：尼哥沒有下限](https://www.ptt.cc/bbs/Gossiping/M.1580252693.A.4EE.html)

[0130 BigLarry：畜生尼哥支那人](https://www.ptt.cc/bbs/Gossiping/M.1580399950.A.9FD.html)

[0130 DASHOCK：尼哥羨慕](https://www.ptt.cc/bbs/Gossiping/M.1580392368.A.3E9.html)

[0130 MAX777：人家是尼哥欸，你是不是種族歧視](https://www.ptt.cc/bbs/Gossiping/M.1580323432.A.DC9.html)

[0130 NCTUcs：尼哥秘書長XDDD](https://www.ptt.cc/bbs/Gossiping/M.1580343091.A.AE4.html)

[0130 TEAJA：尼哥繼續出來護航 又是和平的一天](https://www.ptt.cc/bbs/Gossiping/M.1580314528.A.966.html)

[0130 Win7：尼哥:台灣 who ? RMB真香阿](https://www.ptt.cc/bbs/Gossiping/M.1580355849.A.253.html)

[0130 a126451026：非洲尼哥被看不起活該](https://www.ptt.cc/bbs/Gossiping/M.1580344916.A.7CC.html)

[0130 bartwang：CHO就是尼哥和中國在玩](https://www.ptt.cc/bbs/Gossiping/M.1580383334.A.B9A.html)

[0130 clement80161：收錢的尼哥](https://www.ptt.cc/bbs/Gossiping/M.1580393689.A.365.html)

[0130 doofenshmirz：垃圾尼哥 滾回去種你的棉花](https://www.ptt.cc/bbs/Gossiping/M.1580373890.A.6F8.html)

[0130 eririlover：智障尼哥 腦子被幹壞了膩](https://www.ptt.cc/bbs/Gossiping/M.1580340958.A.A2E.html)

[0130 goldflower：那個尼哥判斷能力騙騙G8AJ還行](https://www.ptt.cc/bbs/Gossiping/M.1580357133.A.B91.html)

[0130 grandwar：垃圾太監組織，用尼哥還太高級了，尼哥](https://www.ptt.cc/bbs/Gossiping/M.1580345661.A.D00.html)

[0130 harry881210：尼哥不意外 被奴役習慣了](https://www.ptt.cc/bbs/Gossiping/M.1580388393.A.D94.html)

[0130 illegalmad：尼哥總統真的不行](https://www.ptt.cc/bbs/Gossiping/M.1580393209.A.E6F.html)

[0130 ilove640：尼哥家人得標的時候](https://www.ptt.cc/bbs/Gossiping/M.1580388619.A.43D.html)

[0130 jeffkent：支那尼哥一直造假，拿摸厲害](https://www.ptt.cc/bbs/Gossiping/M.1580394455.A.19B.html)

[0130 joshddd：尼哥國 ：炸雞好吃](https://www.ptt.cc/bbs/Gossiping/M.1580399489.A.E57.html)

[0130 leoqqqoel：直接說把那個尼哥主習殺了在說](https://www.ptt.cc/bbs/Gossiping/M.1580374185.A.BC9.html)

[0130 ltw89104：給那些尼哥錢錢就沒事了](https://www.ptt.cc/bbs/Gossiping/M.1580382859.A.6F5.html)

[0130 m06m06no1：WHO的尼哥有錢拿連老媽都願意賣](https://www.ptt.cc/bbs/Gossiping/M.1580348571.A.AFF.html)

[0130 moeliliacg：尼哥拿錢就跪舔支那了啊](https://www.ptt.cc/bbs/Gossiping/M.1580316892.A.3B3.html)

[0130 passersK：這個尼哥看了就討厭](https://www.ptt.cc/bbs/Gossiping/M.1580355820.A.428.html)

[0130 sevenine：直接找日本共享就夠了,那個尼哥,膝關節](https://www.ptt.cc/bbs/Gossiping/M.1580382416.A.6C3.html)

[0130 slimfat0202：就是尼哥貪，還用多說](https://www.ptt.cc/bbs/Gossiping/M.1580318033.A.1E9.html)

[0130 soulofring：所以全球意見比不上一個尼哥？](https://www.ptt.cc/bbs/Gossiping/M.1580392045.A.43B.html)

[0130 yashiro：速支那覽啪的尼哥](https://www.ptt.cc/bbs/Gossiping/M.1580354081.A.009.html)

[0131 Gato：中國的棉花田需要引進大量尼哥](https://www.ptt.cc/bbs/Gossiping/M.1580413076.A.E0A.html)

[0131 KUSUHA0707：智障尼哥](https://www.ptt.cc/bbs/Gossiping/M.1580428390.A.413.html)

[0131 Merman19：不想參加了，尼哥的組織](https://www.ptt.cc/bbs/Gossiping/M.1580470385.A.7F7.html)

[0131 MetatronJ：尼哥如果呼吸困難，只要用人民幣當口罩](https://www.ptt.cc/bbs/Gossiping/M.1580460769.A.92C.html)

[0131 PePePeace：舔共覽的尼哥閉嘴](https://www.ptt.cc/bbs/Gossiping/M.1580435600.A.F19.html)

[0131 SuperBMW：尼哥是不是有吃不完的華裔學生妹?! 很拖](https://www.ptt.cc/bbs/Gossiping/M.1580440099.A.158.html)

[0131 aceryu：尼哥邏輯你敢嘴？](https://www.ptt.cc/bbs/Gossiping/M.1580483539.A.77F.html)

[0131 amaranth5566：辣個尼哥幫台灣人提鞋都不夠格](https://www.ptt.cc/bbs/Gossiping/M.1580449671.A.2CC.html)

[0131 deldepress：過的爛衛生紙 第三世界的尼哥 為何永](https://www.ptt.cc/bbs/Gossiping/M.1580408811.A.BC0.html)

[0131 felixr0123：尼哥的心也是黑的不是傳說](https://www.ptt.cc/bbs/Gossiping/M.1580478654.A.94F.html)

[0131 felixr0123：尼哥黑人幫忙改名啊](https://www.ptt.cc/bbs/Gossiping/M.1580443743.A.437.html)

[0131 grafan：尼哥天生賤種真的是不爭的事實](https://www.ptt.cc/bbs/Gossiping/M.1580445563.A.714.html)

[0131 hbj1941：尼哥就不討喜了還舔共](https://www.ptt.cc/bbs/Gossiping/M.1580435743.A.CB3.html)

[0131 hong414：尼哥的國家真的沒必要救助 無情+無義 難](https://www.ptt.cc/bbs/Gossiping/M.1580443991.A.755.html)

[0131 huckebein12：尼哥主席不知道收了幾支炸雞腿](https://www.ptt.cc/bbs/Gossiping/M.1580423939.A.11A.html)

[0131 jeffkent：都沒人討論罷免尼哥](https://www.ptt.cc/bbs/Gossiping/M.1580414613.A.7A8.html)

[0131 jocabyu：尼哥不意外](https://www.ptt.cc/bbs/Gossiping/M.1580418595.A.19C.html)

[0131 k70113：乞丐尼哥又在跪著舔支那懶趴喔？](https://www.ptt.cc/bbs/Gossiping/M.1580482607.A.195.html)

[0131 kenphin0729：尼哥CHO](https://www.ptt.cc/bbs/Gossiping/M.1580442595.A.54A.html)

[0131 kentin：尼哥就適合當奴隸以前當美國人奴隸現在當](https://www.ptt.cc/bbs/Gossiping/M.1580435489.A.F7D.html)

[0131 laukun：尼哥舔屎仔當道](https://www.ptt.cc/bbs/Gossiping/M.1580425775.A.249.html)

[0131 lyk191947：就是個低能尼哥鬼，中共用錢養出來的](https://www.ptt.cc/bbs/Gossiping/M.1580444797.A.ED4.html)

[0131 pikakami：尼哥不意外](https://www.ptt.cc/bbs/Gossiping/M.1580405190.A.3B0.html)

[0131 r85270607：可別說其實是很懂大型企管尼哥](https://www.ptt.cc/bbs/Gossiping/M.1580404125.A.164.html)

[0131 reuentahlv：給土共當夜壺的尼哥](https://www.ptt.cc/bbs/Gossiping/M.1580420230.A.2EC.html)

[0131 rotusea：真的是 尼哥](https://www.ptt.cc/bbs/Gossiping/M.1580431290.A.4EB.html)

[0131 teren：什麼尼哥 人家是堂堂正正的中國人 我幫他噓](https://www.ptt.cc/bbs/Gossiping/M.1580418576.A.586.html)

[0131 tim8177414：非洲尼哥跟我談防疫 去吃土啦](https://www.ptt.cc/bbs/Gossiping/M.1580443992.A.313.html)

[0131 torukumato：尼哥舔共組織](https://www.ptt.cc/bbs/Gossiping/M.1580469137.A.A65.html)

[0131 yeap193：他會說你74尼哥](https://www.ptt.cc/bbs/Gossiping/M.1580484327.A.C7D.html)

[0131 yu1111116：CHO尼哥要跑路去哪裡才不會被追殺](https://www.ptt.cc/bbs/Gossiping/M.1580462480.A.48B.html)

[0131 yudeifish：智障尼哥](https://www.ptt.cc/bbs/Gossiping/M.1580421648.A.21B.html)

[0201 aceryu：拿錢辦事的尼哥組織真他媽骯髒](https://www.ptt.cc/bbs/Gossiping/M.1580560767.A.46C.html)

[0201 cloudpart2：CHO尼哥秘書長:沒事，中國好棒棒](https://www.ptt.cc/bbs/Gossiping/M.1580516098.A.96E.html)

[0201 gunfighter：養一群尼哥小弟 你以為不花錢嗎](https://www.ptt.cc/bbs/Gossiping/M.1580512241.A.FF7.html)

[0201 leoqqqoel：跟本肏你媽垃圾尼哥組織](https://www.ptt.cc/bbs/Gossiping/M.1580561942.A.F2B.html)

[0201 qazws08：那個尼哥組織就不用加了啦...](https://www.ptt.cc/bbs/Gossiping/M.1580533301.A.64D.html)

[0201 richard42：中國投資非洲不少啊 尼哥口袋都人民幣](https://www.ptt.cc/bbs/Gossiping/M.1580492574.A.577.html)

[0201 tigerface：這個尼哥好會舔，根本在毒龍鑽了](https://www.ptt.cc/bbs/Gossiping/M.1580518847.A.CFE.html)

[0202 SuperBMW：害那個CHO尼哥被罵了  爽!!](https://www.ptt.cc/bbs/Gossiping/M.1580646122.A.4D5.html)

[0202 ToTo0306：尼哥幾百年前給白種人奴役，現在給黃種](https://www.ptt.cc/bbs/Gossiping/M.1580612852.A.04D.html)

[0202 achiyeng：不錯啊 是我就直接問候尼哥你老母了](https://www.ptt.cc/bbs/Gossiping/M.1580614837.A.381.html)

[0202 amaranth5566：尼哥你信？](https://www.ptt.cc/bbs/Gossiping/M.1580627099.A.D9D.html)

[0202 aowen：尼哥為了這臭錢把自己搞成歷史罪人 值得麼](https://www.ptt.cc/bbs/Gossiping/M.1580636734.A.0FE.html)

[0202 ash9911911：中國老二吃上癮的尼哥領導的垃圾組織](https://www.ptt.cc/bbs/Gossiping/M.1580623984.A.BC4.html)

[0202 felixr0123：垃圾尼哥 滾回糞坑吃屎](https://www.ptt.cc/bbs/Gossiping/M.1580653947.A.F31.html)

[0202 kerrygabriel：尼哥](https://www.ptt.cc/bbs/Gossiping/M.1580616136.A.6AB.html)

[0202 ufap：尼哥最愛維尼](https://www.ptt.cc/bbs/Gossiping/M.1580627515.A.9C0.html)

[0202 widec：別怪他 非洲尼哥當然會覺得中國已經好棒棒](https://www.ptt.cc/bbs/Gossiping/M.1580654923.A.031.html)

[0202 wulaw5566：垃圾尼哥](https://www.ptt.cc/bbs/Gossiping/M.1580611844.A.913.html)

[0203 KUSUHA0707：智障尼哥都能當秘書長了](https://www.ptt.cc/bbs/Gossiping/M.1580714796.A.639.html)

[0203 MK47：尼哥只要有錢什麼話都說的出口](https://www.ptt.cc/bbs/Gossiping/M.1580726567.A.A98.html)

[0203 dlevel：尼哥不是說中國表現很好，可以控制狀況](https://www.ptt.cc/bbs/Gossiping/M.1580722722.A.02A.html)

[0203 dswing：就比中國公衛更落後的尼哥當然相信中國啊](https://www.ptt.cc/bbs/Gossiping/M.1580682522.A.15D.html)

[0203 haru97724：尼哥閉嘴啦](https://www.ptt.cc/bbs/Gossiping/M.1580733256.A.B5E.html)

[0203 kenslc199：支那尼哥賤畜嘴臉有夠難看](https://www.ptt.cc/bbs/Gossiping/M.1580734012.A.FC0.html)

[0203 ldstar：尼哥跟韓粉英粉並列世界三大智障人種](https://www.ptt.cc/bbs/Gossiping/M.1580712553.A.DFA.html)

[0203 scum5566：垃圾尼哥](https://www.ptt.cc/bbs/Gossiping/M.1580739080.A.715.html)

[0203 zzshcool：唉唷kmt啊 不是尼哥？](https://www.ptt.cc/bbs/Gossiping/M.1580737358.A.D93.html)

[0204 Auoer：尼哥](https://www.ptt.cc/bbs/Gossiping/M.1580818565.A.1B5.html)

[0204 ComfortPTT：尼哥又不會理你](https://www.ptt.cc/bbs/Gossiping/M.1580785855.A.B75.html)

[0204 JHNJHNJHN：希望是尼哥在舔習的時候被傳染的](https://www.ptt.cc/bbs/Gossiping/M.1580797951.A.EED.html)

[0204 Lenney33：CHO繼續舔,世各國早沒人鳥你這個尼哥惹](https://www.ptt.cc/bbs/Gossiping/M.1580762084.A.CA2.html)

[0204 NNBOY：智障尼哥幹你娘到底有沒有腦](https://www.ptt.cc/bbs/Gossiping/M.1580826088.A.7AE.html)

[0204 YuenYang5566：乞丐黑人尼哥，只會搖尾憐乞 可憐](https://www.ptt.cc/bbs/Gossiping/M.1580783015.A.A1B.html)

[0204 alrin891202：哪來的尼哥](https://www.ptt.cc/bbs/Gossiping/M.1580831498.A.994.html)

[0204 drcula：尼哥搞不好中標了](https://www.ptt.cc/bbs/Gossiping/M.1580820404.A.F84.html)

[0204 eva19452002：因為黑人尼哥欠阿共很多錢](https://www.ptt.cc/bbs/Gossiping/M.1580787500.A.672.html)

[0204 ggian123：幹你娘的 跟垃圾尼哥一搭一唱](https://www.ptt.cc/bbs/Gossiping/M.1580809469.A.8FF.html)

[0204 kt9701：要怎樣做才能罷免尼哥????](https://www.ptt.cc/bbs/Gossiping/M.1580825890.A.290.html)

[0204 peter105096：收支那前的尼哥秘書長什麼時候下來啊](https://www.ptt.cc/bbs/Gossiping/M.1580791173.A.A4E.html)

[0204 slovea：沒人在乎尼哥說了什麼](https://www.ptt.cc/bbs/Gossiping/M.1580785337.A.882.html)

[0204 swatseal：非洲尼哥就算沒有武漢肺炎 還有伊波拉跟](https://www.ptt.cc/bbs/Gossiping/M.1580783349.A.854.html)

[0204 vgil：垃圾尼哥](https://www.ptt.cc/bbs/Gossiping/M.1580793432.A.F8F.html)

[0204 wanters：我還以為是尼哥 這支是誰啊?](https://www.ptt.cc/bbs/Gossiping/M.1580793374.A.7ED.html)

[0205 DouglasT：尼哥仔說服的了美國人我就信你一次](https://www.ptt.cc/bbs/Gossiping/M.1580872115.A.396.html)

[0205 LordOfCS：幹你娘智障尼哥](https://www.ptt.cc/bbs/Gossiping/M.1580871369.A.198.html)

[0205 OdinSword：尼哥閉嘴](https://www.ptt.cc/bbs/Gossiping/M.1580915807.A.6DA.html)

[0205 Xellowse2：尼哥B嘴](https://www.ptt.cc/bbs/Gossiping/M.1580837756.A.6CD.html)

[0205 altecsrs：尼哥每天都要想梗，真辛苦](https://www.ptt.cc/bbs/Gossiping/M.1580896447.A.230.html)

[0205 bala73：跟CHO尼哥的樣子一樣呢](https://www.ptt.cc/bbs/Gossiping/M.1580887347.A.DA6.html)

[0205 mlnaml123：跟米國爸爸好比較有用，尼哥只會死要錢](https://www.ptt.cc/bbs/Gossiping/M.1580900779.A.7FD.html)

[0205 nathan2000：那個尼哥怎麼看都是個白痴，黑人之恥.](https://www.ptt.cc/bbs/Gossiping/M.1580872982.A.494.html)

[0205 onollll：垃圾尼哥 應該全部殺光](https://www.ptt.cc/bbs/Gossiping/M.1580863520.A.DA4.html)

[0205 swatseal：那些低端尼哥沒飯吃關他屁事 你覺得這種](https://www.ptt.cc/bbs/Gossiping/M.1580877317.A.CB8.html)

[0205 ting74942：尼哥說的話也信](https://www.ptt.cc/bbs/Gossiping/M.1580880694.A.9AE.html)

[0205 zzff92：垃圾尼哥不意外](https://www.ptt.cc/bbs/Gossiping/M.1580869432.A.754.html)

[0206 Gargila0135：幹你娘衣索比亞尼哥及周邊尼哥地區](https://www.ptt.cc/bbs/Gossiping/M.1580949698.A.3F4.html)

[0206 Kowdan：尼哥版國瑜](https://www.ptt.cc/bbs/Gossiping/M.1580962693.A.C6A.html)

[0206 a27783322：叫那個尼哥下台 看到他就賭爛](https://www.ptt.cc/bbs/Gossiping/M.1580983478.A.199.html)

[0206 d125383957：政治歸政治  尼哥歸尼哥](https://www.ptt.cc/bbs/Gossiping/M.1580996592.A.C9F.html)

[0206 gustavvv：尼哥：14億>30萬](https://www.ptt.cc/bbs/Gossiping/M.1580958999.A.D45.html)

[0206 hw1：尼哥勾結共匪要來撈錢了](https://www.ptt.cc/bbs/Gossiping/M.1580960559.A.819.html)

[0206 kobala：尼哥 快出來說你收多少R](https://www.ptt.cc/bbs/Gossiping/M.1580949613.A.617.html)

[0206 lastchristma：尼哥肉便器  我看就該全家抓去中國](https://www.ptt.cc/bbs/Gossiping/M.1580962196.A.BAB.html)

[0206 pikakami：尼哥把持的組織沒什麼用](https://www.ptt.cc/bbs/Gossiping/M.1580967745.A.52D.html)

[0206 vking223：黑人尼哥討錢總是十分有效率](https://www.ptt.cc/bbs/Gossiping/M.1580970423.A.1D4.html)

[0206 voyage0131：這個尼哥真的發大財](https://www.ptt.cc/bbs/Gossiping/M.1580955369.A.8A9.html)

[0207 Omara：那些尼哥部落國家真的去死一死比較快](https://www.ptt.cc/bbs/Gossiping/M.1581038561.A.D8C.html)

[0207 PChair：去吃炸雞啦尼哥](https://www.ptt.cc/bbs/Gossiping/M.1581083136.A.2FB.html)

[0207 amaranth5566：尼哥支那人](https://www.ptt.cc/bbs/Gossiping/M.1581063975.A.1F2.html)

[0207 eightyseven：尼哥回去採收咖啡豆好嗎 少在這邊亂](https://www.ptt.cc/bbs/Gossiping/M.1581065184.A.FFE.html)

[0207 f8954017：？？突然？？尼哥被換掉了？](https://www.ptt.cc/bbs/Gossiping/M.1581089281.A.F1F.html)

[0207 gay7788：順便把尼哥拉下台](https://www.ptt.cc/bbs/Gossiping/M.1581040139.A.FE4.html)

[0207 grafan：嘴砲尼哥 真的是低等人種](https://www.ptt.cc/bbs/Gossiping/M.1581081910.A.BC8.html)

[0207 hy23：今天變成這樣 尼哥是世界罪人](https://www.ptt.cc/bbs/Gossiping/M.1581084121.A.EA8.html)

[0207 physicsdk：尼哥也有不少拉雞啊，WHO那位金母湯](https://www.ptt.cc/bbs/Gossiping/M.1581081315.A.F80.html)

[0207 willy0206：那個尼哥老大是薩諾斯吧](https://www.ptt.cc/bbs/Gossiping/M.1581065863.A.960.html)

[0207 winteryoyo：尼哥交叉感染給中國伊波拉 剛好而已](https://www.ptt.cc/bbs/Gossiping/M.1581059553.A.E5C.html)

[0207 ymcaboy：懂了，原來舉國衣索比亞的尼哥都這副尿性](https://www.ptt.cc/bbs/Gossiping/M.1581037896.A.00C.html)

[0208 Beltran：只有CHO尼哥說不算 有差嗎](https://www.ptt.cc/bbs/Gossiping/M.1581136407.A.B89.html)

[0208 KUSUHA0707：who尼哥舔人民幣可爽了](https://www.ptt.cc/bbs/Gossiping/M.1581158016.A.098.html)

[0208 jeffkent：不會有人理支那尼哥的廢言](https://www.ptt.cc/bbs/Gossiping/M.1581150889.A.872.html)

[0208 jimling2001：垃圾尼哥](https://www.ptt.cc/bbs/Gossiping/M.1581134071.A.1CC.html)

[0208 jk01：WHO尼哥都說小病而已](https://www.ptt.cc/bbs/Gossiping/M.1581118570.A.0D9.html)

[0208 laicyun：尼哥閉嘴啦](https://www.ptt.cc/bbs/Gossiping/M.1581148212.A.FB8.html)

[0208 sky6969：=========== 垃圾尼哥幹你娘 ===========](https://www.ptt.cc/bbs/Gossiping/M.1581115081.A.6DD.html)

[0208 sux0116：尼哥閉嘴](https://www.ptt.cc/bbs/Gossiping/M.1581162514.A.0B1.html)

[0208 vking223：去你的尼哥，當初誰跟全球各國說不嚴重](https://www.ptt.cc/bbs/Gossiping/M.1581144355.A.6F6.html)

[0208 zxzzzzzzzzzz：非洲尼哥道德標準低](https://www.ptt.cc/bbs/Gossiping/M.1581134801.A.1BC.html)

[0209 allmygod：中共養的尼哥走狗集團可以聽媽](https://www.ptt.cc/bbs/Gossiping/M.1581232889.A.E14.html)

[0209 eyesg：哇 原來是有前科的尼哥](https://www.ptt.cc/bbs/Gossiping/M.1581227112.A.E15.html)

[0209 frfreedom：龜頭香嗎 尼哥](https://www.ptt.cc/bbs/Gossiping/M.1581212713.A.FD2.html)

[0209 highyes：尼哥被習包帝肛過](https://www.ptt.cc/bbs/Gossiping/M.1581207494.A.6B0.html)

[0209 jeffkent：google和FB絕對不可能鳥這隻支那尼哥](https://www.ptt.cc/bbs/Gossiping/M.1581218375.A.A0D.html)

[0209 justin81828：尼哥去吃屎](https://www.ptt.cc/bbs/Gossiping/M.1581245099.A.044.html)

[0209 kenndy：尼哥b嘴，都不怕報應?](https://www.ptt.cc/bbs/Gossiping/M.1581232005.A.1BD.html)

[0209 nk101：問世衛那個尼哥。等等他會幫忙認證。](https://www.ptt.cc/bbs/Gossiping/M.1581256687.A.D2B.html)

[0209 revorea：進去要捐錢救打壓我們的尼哥跟支那，何必](https://www.ptt.cc/bbs/Gossiping/M.1581208967.A.904.html)

[0209 soxgo：尼哥就是尼哥 人民幣真香 舔好舔滿](https://www.ptt.cc/bbs/Gossiping/M.1581250524.A.3A7.html)

[0209 z540123：尼哥出來玩了](https://www.ptt.cc/bbs/Gossiping/M.1581257439.A.479.html)

[0210 BAR21：就讓尼哥支那賤畜猶太人白雜碎被痰淹死就好](https://www.ptt.cc/bbs/Gossiping/M.1581320829.A.878.html)

[0210 Bigcookie2：幹你尼哥自己不會去喔 垃圾](https://www.ptt.cc/bbs/Gossiping/M.1581293577.A.509.html)

[0210 Kowdan：讓支那跟垃圾尼哥死一死就好](https://www.ptt.cc/bbs/Gossiping/M.1581303933.A.9E2.html)

[0210 antibody27：尼哥繼續舔啊](https://www.ptt.cc/bbs/Gossiping/M.1581297875.A.3F4.html)

[0210 elec1141：尼哥威武](https://www.ptt.cc/bbs/Gossiping/M.1581295949.A.7EA.html)

[0210 freddy8317：fuck 尼哥 垃圾國](https://www.ptt.cc/bbs/Gossiping/M.1581334054.A.1E0.html)

[0210 goldflower：要去 垃圾尼哥組織](https://www.ptt.cc/bbs/Gossiping/M.1581309029.A.3FB.html)

[0210 hw1：你要不要自殺謝罪啊 垃圾尼哥](https://www.ptt.cc/bbs/Gossiping/M.1581335948.A.543.html)

[0210 la8day：中國和尼哥這次聯手報復世界](https://www.ptt.cc/bbs/Gossiping/M.1581307188.A.E8B.html)

[0210 learnpig：你媽的，讓尼哥跟賤畜自己去玩就好了，](https://www.ptt.cc/bbs/Gossiping/M.1581320447.A.898.html)

[0210 paul2chiu：尼哥：中國造福他國 防止疫情擴散](https://www.ptt.cc/bbs/Gossiping/M.1581325968.A.071.html)

[0210 repast：垃圾尼哥](https://www.ptt.cc/bbs/Gossiping/M.1581299472.A.7F1.html)

[0210 scum5566：WHO尼哥才不會理他](https://www.ptt.cc/bbs/Gossiping/M.1581330761.A.696.html)

[0210 tsming：香港母豬後面放一隻尼哥](https://www.ptt.cc/bbs/Gossiping/M.1581349507.A.217.html)

[0210 vking223：聽命who尼哥幫才作反應穩死](https://www.ptt.cc/bbs/Gossiping/M.1581316388.A.A8A.html)

[0210 wolfking：不過他又不在尼哥日亞](https://www.ptt.cc/bbs/Gossiping/M.1581350089.A.120.html)

[0210 xcv591：尼哥水準啊](https://www.ptt.cc/bbs/Gossiping/M.1581268850.A.81F.html)

[0210 yashiro：尼哥會長應斬首示眾](https://www.ptt.cc/bbs/Gossiping/M.1581307141.A.0C5.html)

[0210 yeap193：尼哥就先+10分了](https://www.ptt.cc/bbs/Gossiping/M.1581336794.A.07F.html)

[0211 PePePeace：舔共覽的尼哥](https://www.ptt.cc/bbs/Gossiping/M.1581394313.A.B4A.html)

[0211 bbdirty5566：美國爸爸也是尼哥居多阿](https://www.ptt.cc/bbs/Gossiping/M.1581388449.A.581.html)

[0211 fajita：尼哥舔汁肺炎](https://www.ptt.cc/bbs/Gossiping/M.1581435887.A.147.html)

[0211 jiangjiang33：乞丐尼哥](https://www.ptt.cc/bbs/Gossiping/M.1581376509.A.812.html)

[0211 mack860120：讚啦 跟那垃圾尼哥掌控的CHO不一樣](https://www.ptt.cc/bbs/Gossiping/M.1581391893.A.425.html)

[0211 skygray2：那群種棉花的尼哥絕對不會讓你發言的](https://www.ptt.cc/bbs/Gossiping/M.1581399052.A.8E7.html)

[0212 BigLarry：CHO尼哥也這樣想 人民幣 代表的就是愛](https://www.ptt.cc/bbs/Gossiping/M.1581487859.A.733.html)

[0212 Flyshinesky：尼哥變風向？CHO不是說控制很好](https://www.ptt.cc/bbs/Gossiping/M.1581460308.A.E9D.html)

[0212 Hall：尼哥在怎麼蠢也知道美中二選一要聽誰的 論科](https://www.ptt.cc/bbs/Gossiping/M.1581465006.A.C07.html)

[0212 Lenney33：不是支那肺炎嗎 尼哥？](https://www.ptt.cc/bbs/Gossiping/M.1581439009.A.EC9.html)

[0212 cygnusx123：垃圾尼哥，看看以前說的屎話](https://www.ptt.cc/bbs/Gossiping/M.1581518480.A.64C.html)

[0212 ezorttc：叫你家尼哥出來說話](https://www.ptt.cc/bbs/Gossiping/M.1581506243.A.066.html)

[0212 ymcaboy：MERS 中東就好欺負逆？垃圾尼哥](https://www.ptt.cc/bbs/Gossiping/M.1581476283.A.98D.html)

[0213 Eligor41：尼哥指導先進國軍的衛生你奈我何](https://www.ptt.cc/bbs/Gossiping/M.1581554195.A.27B.html)

[0213 chris1281：舔共譚德賽，尼哥到底拿了中國多少錢？](https://www.ptt.cc/bbs/Gossiping/M.1581551310.A.56E.html)

[0213 jas78901：尼哥可憐哪](https://www.ptt.cc/bbs/Gossiping/M.1581559478.A.A52.html)

[0213 jasonRichard：白痴尼哥](https://www.ptt.cc/bbs/Gossiping/M.1581587562.A.79F.html)

[0213 ohrring：尼哥不會數學這是常識](https://www.ptt.cc/bbs/Gossiping/M.1581560151.A.5BB.html)

[0213 s820912gmail：尼哥去死啦](https://www.ptt.cc/bbs/Gossiping/M.1581572230.A.4AD.html)

[0214 Yuwuen：尼哥不要你的臭美金 只要人民幣](https://www.ptt.cc/bbs/Gossiping/M.1581654905.A.3E1.html)

[0214 cijaytheone：尼哥也可以有...中國夢好嗎？](https://www.ptt.cc/bbs/Gossiping/M.1581646722.A.8AF.html)

[0214 tsming：現在靠自己靠美國，不太想理那個尼哥組織](https://www.ptt.cc/bbs/Gossiping/M.1581693558.A.FE9.html)

[0214 yjjia：尼哥的flag](https://www.ptt.cc/bbs/Gossiping/M.1581681794.A.C8C.html)

[0215 chennylee809：尼哥還是去採棉花種咖啡豆吧](https://www.ptt.cc/bbs/Gossiping/M.1581767946.A.F1E.html)

[0215 renee4：X尼哥...](https://www.ptt.cc/bbs/Gossiping/M.1581739215.A.69A.html)

[0215 vwpassat：尼哥官員的私人帳戶匯錢。](https://www.ptt.cc/bbs/Gossiping/M.1581782367.A.6BB.html)

[0216 ak904：尼哥繼續舔](https://www.ptt.cc/bbs/Gossiping/M.1581825155.A.1D6.html)

[0216 allmygod：尼哥不是這樣說的嗎](https://www.ptt.cc/bbs/Gossiping/M.1581832188.A.BD7.html)

[0216 iPadProPlus：尼哥舔共組織](https://www.ptt.cc/bbs/Gossiping/M.1581831511.A.040.html)

[0216 locer：就低能尼哥](https://www.ptt.cc/bbs/Gossiping/M.1581826459.A.8D4.html)

[0216 snapdragon：垃圾尼哥就是賤](https://www.ptt.cc/bbs/Gossiping/M.1581824842.A.6C9.html)

[0216 soulofring：尼哥去死](https://www.ptt.cc/bbs/Gossiping/M.1581818548.A.D65.html)

[0216 tsming：這種尼哥組織不用加入了](https://www.ptt.cc/bbs/Gossiping/M.1581825118.A.1D6.html)

[0217 XXXXSOW：幹你娘垃圾尼哥組織 滾去種棉花](https://www.ptt.cc/bbs/Gossiping/M.1581940673.A.EC9.html)

[0217 jameswen：垃圾尼哥](https://www.ptt.cc/bbs/Gossiping/M.1581922930.A.CF2.html)

[0217 p95649564：抽一個尼哥](https://www.ptt.cc/bbs/Gossiping/M.1581910595.A.159.html)

[0218 Omara：這幾個垃圾尼哥要不要切腹謝罪？](https://www.ptt.cc/bbs/Gossiping/M.1581956904.A.129.html)

[0218 a0921387223：看到這個尼哥就一肚子火](https://www.ptt.cc/bbs/Gossiping/M.1581982815.A.862.html)

[0218 charlie2010：黑人尼哥怎麼還沒得肺炎](https://www.ptt.cc/bbs/Gossiping/M.1581983039.A.917.html)

[0218 gay7788：尼哥還是B嘴ㄅ](https://www.ptt.cc/bbs/Gossiping/M.1582012695.A.397.html)

[0218 hanbingsiji：尼哥組織誰要](https://www.ptt.cc/bbs/Gossiping/M.1581963696.A.23D.html)

[0218 huabandd：不要加入 垃圾組織 低能尼哥](https://www.ptt.cc/bbs/Gossiping/M.1582041442.A.E52.html)

[0218 mack860120：尼哥正常發揮](https://www.ptt.cc/bbs/Gossiping/M.1582004837.A.6C5.html)

[0218 stw0975：低能尼哥](https://www.ptt.cc/bbs/Gossiping/M.1582031153.A.E13.html)

[0218 tomhlover：尼哥是在怕殺小 不是說很安全](https://www.ptt.cc/bbs/Gossiping/M.1582000421.A.242.html)

[0219 Arad：淦智障尼哥你自己去吃毒吧](https://www.ptt.cc/bbs/Gossiping/M.1582076211.A.2CB.html)

[0219 ak904：黑人尼哥當頭你能期待什麼？](https://www.ptt.cc/bbs/Gossiping/M.1582078594.A.684.html)

[0219 vking223：黑人尼哥總幹事繼續充耳不聞](https://www.ptt.cc/bbs/Gossiping/M.1582077305.A.F0D.html)

[0219 wanters：尼哥:我們今天起定義中國為世上最清潔](https://www.ptt.cc/bbs/Gossiping/M.1582124157.A.68A.html)

[0220 akt133：非洲尼哥 你還是回去非洲嗚嗚哈哈的叫就好](https://www.ptt.cc/bbs/Gossiping/M.1582176441.A.225.html)

[0220 antibody27：垃圾尼哥真不要臉](https://www.ptt.cc/bbs/Gossiping/M.1582154538.A.D4E.html)

[0220 greedypeople：STFU 尼哥](https://www.ptt.cc/bbs/Gossiping/M.1582173861.A.94B.html)

[0221 a176893：因為三胖不聽你尼哥的話啊幹](https://www.ptt.cc/bbs/Gossiping/M.1582280687.A.42C.html)

[0221 fajita：尼哥怎麼改口啦？要不要改稱尼哥肺炎？](https://www.ptt.cc/bbs/Gossiping/M.1582255705.A.5F4.html)

[0221 krthree：尼哥：高評價。ok ok.  我的帳號在這。](https://www.ptt.cc/bbs/Gossiping/M.1582296293.A.983.html)

[0222 OOQ：尼哥再繼續舔支那啊](https://www.ptt.cc/bbs/Gossiping/M.1582332656.A.0E4.html)

[0222 crusoe：有沒可能是尼哥收阿共錢？](https://www.ptt.cc/bbs/Gossiping/M.1582343032.A.933.html)

[0222 jojo90320：我越來越相信尼哥智商都很低了](https://www.ptt.cc/bbs/Gossiping/M.1582327400.A.F1F.html)

[0222 kkoo5888：尼哥人黑心也黑](https://www.ptt.cc/bbs/Gossiping/M.1582372558.A.1EA.html)

[0222 rainylife：希望之窗不就那個尼哥縮小的，再鼓勵旅](https://www.ptt.cc/bbs/Gossiping/M.1582361930.A.B77.html)

[0223 misu2718：呵呵，尼哥說阿共做的很好，大家要感謝](https://www.ptt.cc/bbs/Gossiping/M.1582419175.A.03E.html)

[0224 antibody27：稀罕嗎我呸黑鬼尼哥吃屎](https://www.ptt.cc/bbs/Gossiping/M.1582534514.A.CDE.html)

[0224 grandwar：CHO尼哥先去自殺負責再來談防疫，反正對](https://www.ptt.cc/bbs/Gossiping/M.1582476462.A.B10.html)

[0224 peter105096：尼哥口袋裝滿了維尼的黃金](https://www.ptt.cc/bbs/Gossiping/M.1582522008.A.053.html)

[0224 requan：幹，就一開始cho尼哥要大家放心去中國害](https://www.ptt.cc/bbs/Gossiping/M.1582529929.A.78E.html)

[0225 AVR0：CHO尼哥到底收了多少？](https://www.ptt.cc/bbs/Gossiping/M.1582635945.A.738.html)

[0225 NgJovi：這個尼哥真的是](https://www.ptt.cc/bbs/Gossiping/M.1582640099.A.C4F.html)

[0225 TaiwanGeorge：尼哥都不尼哥了，丟尼哥的臉。](https://www.ptt.cc/bbs/Gossiping/M.1582590656.A.112.html)

[0225 calance：尼哥唸摳v的奶挺啊](https://www.ptt.cc/bbs/Gossiping/M.1582643302.A.9AF.html)

[0225 hsunting2000：尼哥從早講到現在快閉嘴拉](https://www.ptt.cc/bbs/Gossiping/M.1582609886.A.2E8.html)

[0225 kixer2005：尼哥吃屎幹](https://www.ptt.cc/bbs/Gossiping/M.1582599111.A.847.html)

[0225 logitech2004：尼哥真的是最低等的種族，天生就是](https://www.ptt.cc/bbs/Gossiping/M.1582644329.A.335.html)

[0225 nzsrr：尼哥不可信。](https://www.ptt.cc/bbs/Gossiping/M.1582598025.A.55B.html)

[0225 shawn11：很嚴重然後說中國好話 這是尼哥邏輯？](https://www.ptt.cc/bbs/Gossiping/M.1582562101.A.077.html)

[0225 suijojo：幫武漢QQ，尼哥已經暗示得很清楚了](https://www.ptt.cc/bbs/Gossiping/M.1582646229.A.755.html)

[0225 watermen：黑鬼尼哥吃屎去吧](https://www.ptt.cc/bbs/Gossiping/M.1582594742.A.8DD.html)

[0226 DarkerDuck：講這種話都不會臉紅，啊原來是尼哥](https://www.ptt.cc/bbs/Gossiping/M.1582722217.A.EE5.html)

[0226 Yuwuen：這個尼哥有收人民幣](https://www.ptt.cc/bbs/Gossiping/M.1582732732.A.F3A.html)

[0226 abckk：先讓尼哥拉一下世界仇恨值，等背後操控的](https://www.ptt.cc/bbs/Gossiping/M.1582679432.A.DF6.html)

[0226 airider：支那人養的尼哥奴才](https://www.ptt.cc/bbs/Gossiping/M.1582726851.A.92D.html)

[0226 dovepacket：尼哥:大家要值得感謝WHo](https://www.ptt.cc/bbs/Gossiping/M.1582681138.A.589.html)

[0226 juyac11：w h o會這麼爛還不是因為中國小弟尼哥在](https://www.ptt.cc/bbs/Gossiping/M.1582692331.A.61B.html)

[0226 kada9999：尼哥組織](https://www.ptt.cc/bbs/Gossiping/M.1582679736.A.5AB.html)

[0226 ms0545173：尼哥舔共舔到忘記擦嘴巴](https://www.ptt.cc/bbs/Gossiping/M.1582701291.A.248.html)

[0226 pikakami：有錢買通WHO的尼哥  沒錢救武漢  哈哈哈](https://www.ptt.cc/bbs/Gossiping/M.1582647620.A.7A7.html)

[0226 pikakami：選個尼哥出來就是錯誤了](https://www.ptt.cc/bbs/Gossiping/M.1582648100.A.BAB.html)

[0226 schooldance：不想加入這個垃圾尼哥組織...](https://www.ptt.cc/bbs/Gossiping/M.1582724673.A.006.html)

[0226 tenka92417：這位是尊貴不凡的白人，不是尼哥](https://www.ptt.cc/bbs/Gossiping/M.1582680204.A.B89.html)

[0226 tku9527：尼哥的建議啊](https://www.ptt.cc/bbs/Gossiping/M.1582715651.A.21A.html)

[0227 Brook74627：垃圾尼哥](https://www.ptt.cc/bbs/Gossiping/M.1582764036.A.E47.html)

[0227 FLy60169：尼哥](https://www.ptt.cc/bbs/Gossiping/M.1582789701.A.DAA.html)

[0227 Tim1107：尼哥](https://www.ptt.cc/bbs/Gossiping/M.1582791343.A.EEC.html)

[0227 inshadow：尼哥天性就是奴隸 根本不能當領袖](https://www.ptt.cc/bbs/Gossiping/M.1582795380.A.3D4.html)

[0227 krthree：不用參加，讓尼哥嚐嚐中國的汕液](https://www.ptt.cc/bbs/Gossiping/M.1582784320.A.A2D.html)

[0227 revise：尼哥：not yet](https://www.ptt.cc/bbs/Gossiping/M.1582769225.A.4E7.html)

[0228 Jeff9453：垃圾尼哥 畜生支那](https://www.ptt.cc/bbs/Gossiping/M.1582862541.A.E56.html)

[0228 b93510015：尼哥真的是夠爛了](https://www.ptt.cc/bbs/Gossiping/M.1582843541.A.7AE.html)

[0228 child1991：可以進去看那些尼哥耍寶啊](https://www.ptt.cc/bbs/Gossiping/M.1582854797.A.AE4.html)

[0228 ktoaoeex：垃圾尼哥](https://www.ptt.cc/bbs/Gossiping/M.1582849454.A.C96.html)

[0228 mcut914010：尼哥：錢錢…](https://www.ptt.cc/bbs/Gossiping/M.1582904848.A.AF7.html)

[0229 Joybena：尼哥廢物](https://www.ptt.cc/bbs/Gossiping/M.1582909573.A.464.html)

[0229 abckk：尼哥報復世界計画通り](https://www.ptt.cc/bbs/Gossiping/M.1582908861.A.C9F.html)

[0229 aowen：為什麼會給一個智障尼哥當上秘書長？](https://www.ptt.cc/bbs/Gossiping/M.1582907377.A.425.html)

[0229 child1991：全世界都看出來了就你這白癡尼哥不知道](https://www.ptt.cc/bbs/Gossiping/M.1582958505.A.F4D.html)

[0229 ironkyoater：尼哥：中國他媽還不打錢過來？](https://www.ptt.cc/bbs/Gossiping/M.1582940043.A.E6A.html)

[0229 radi035：WHO垃圾尼哥 怎麼不去死啦 幹](https://www.ptt.cc/bbs/Gossiping/M.1582950408.A.01D.html)

[0229 voyage0131：尼哥都被連署要他下台了 可悲的kmt老](https://www.ptt.cc/bbs/Gossiping/M.1582930337.A.C46.html)

[0229 wellwest：尼哥水準不意外](https://www.ptt.cc/bbs/Gossiping/M.1582961169.A.E14.html)

[0301 HELLDIVER：CHO尼哥:大家要洩洩中國人啊](https://www.ptt.cc/bbs/Gossiping/M.1583035043.A.1E4.html)

[0301 PttNoMoney：尼哥舔維尼組織](https://www.ptt.cc/bbs/Gossiping/M.1583022823.A.ED2.html)

[0301 ezorttc：尼哥已經躲起來了，免得被伊朗姦殺](https://www.ptt.cc/bbs/Gossiping/M.1583073891.A.7FB.html)

[0301 pickoff：非洲尼哥當家 靠中國吃餅 可憐那](https://www.ptt.cc/bbs/Gossiping/M.1583072763.A.176.html)

[0302 XXXXSOW：現在才知道who根本尼哥賤種組織](https://www.ptt.cc/bbs/Gossiping/M.1583158267.A.5B3.html)

[0302 child1991：所以這個白癡尼哥不是第一次害死人了](https://www.ptt.cc/bbs/Gossiping/M.1583144098.A.863.html)

[0302 ejirmpu：尼哥](https://www.ptt.cc/bbs/Gossiping/M.1583117747.A.85F.html)

[0303 c6587924：尼哥繼續捧](https://www.ptt.cc/bbs/Gossiping/M.1583208746.A.CA6.html)

[0303 gracew0709：尼哥基因就不意外 整天只想貪小便宜](https://www.ptt.cc/bbs/Gossiping/M.1583203957.A.C16.html)

[0303 jimling2001：尼哥閉嘴](https://www.ptt.cc/bbs/Gossiping/M.1583218180.A.C38.html)

[0303 ktoaoeex：被這垃圾尼哥坑了一個多月也該醒了](https://www.ptt.cc/bbs/Gossiping/M.1583232438.A.D58.html)

[0303 light20735：87尼哥怎麼不去死](https://www.ptt.cc/bbs/Gossiping/M.1583243196.A.DC4.html)

[0303 nzej723yyip：尼哥中的恥辱](https://www.ptt.cc/bbs/Gossiping/M.1583224930.A.93B.html)

[0303 seekeve：我只希望這個尼哥早點下台](https://www.ptt.cc/bbs/Gossiping/M.1583197858.A.0C6.html)

[0303 shortimex：尼哥真的狂舔](https://www.ptt.cc/bbs/Gossiping/M.1583242293.A.B1B.html)

[0303 sid3：這位尼哥是地府來的吧](https://www.ptt.cc/bbs/Gossiping/M.1583200584.A.12B.html)

[0303 slovea：尼哥去給狗幹一幹啦](https://www.ptt.cc/bbs/Gossiping/M.1583229429.A.1D8.html)

[0303 t88002：垃圾尼哥害慘全世界](https://www.ptt.cc/bbs/Gossiping/M.1583240917.A.238.html)

[0304 Koibito：低能尼哥](https://www.ptt.cc/bbs/Gossiping/M.1583324975.A.E42.html)

[0304 TarikBlack：低端尼哥不懂啦，他只想要錢](https://www.ptt.cc/bbs/Gossiping/M.1583325976.A.265.html)

[0304 ahy：垃圾尼哥](https://www.ptt.cc/bbs/Gossiping/M.1583289887.A.AC0.html)

[0304 coolstart：尼哥說幹話，汪汪汪](https://www.ptt.cc/bbs/Gossiping/M.1583313933.A.6F7.html)

[0304 kt9701：尼哥跟他的伙伴維尼](https://www.ptt.cc/bbs/Gossiping/M.1583335790.A.692.html)

[0304 meowyu：尼哥一定甩鍋給日本政府啦](https://www.ptt.cc/bbs/Gossiping/M.1583285272.A.185.html)

[0304 okitawawa：爆成這樣都沒有國家想削那個黑人尼哥](https://www.ptt.cc/bbs/Gossiping/M.1583329228.A.690.html)

[0304 rainylife：尼哥生日關大家屁事? 要幫唱生日快樂歌](https://www.ptt.cc/bbs/Gossiping/M.1583275149.A.50E.html)

[0305 william7727：這個尼哥必噓](https://www.ptt.cc/bbs/Gossiping/M.1583417657.A.572.html)

[0306 ECZEMA：先進國會不爽，但非洲尼哥票票等值](https://www.ptt.cc/bbs/Gossiping/M.1583495617.A.756.html)

[0306 dyrhue1126：看到尼哥秘書長你覺得有差嗎..](https://www.ptt.cc/bbs/Gossiping/M.1583428706.A.237.html)

[0306 gincod：還想搞啊尼哥](https://www.ptt.cc/bbs/Gossiping/M.1583477297.A.4F8.html)

[0306 jessicali：畢竟尼哥窮好欺負](https://www.ptt.cc/bbs/Gossiping/M.1583467553.A.914.html)

[0306 poqwiuer：尼哥舔的很開心 叫牠非洲豬奴都行](https://www.ptt.cc/bbs/Gossiping/M.1583467850.A.1C4.html)

[0307 BAR21：全球尼哥猶太人支那賤畜白垃圾比不過一個小](https://www.ptt.cc/bbs/Gossiping/M.1583592284.A.816.html)

[0307 bdbpzcatqpq：尼哥又調皮惹](https://www.ptt.cc/bbs/Gossiping/M.1583561558.A.B2B.html)

[0307 l42857：你知道尼哥是誰幫忙上位的嗎？](https://www.ptt.cc/bbs/Gossiping/M.1583552870.A.B4B.html)

[0307 soxgo：全世界真的被中國和尼哥害死](https://www.ptt.cc/bbs/Gossiping/M.1583579447.A.DDC.html)

[0307 vaiking0120：對抗中國和他的尼哥朋友？](https://www.ptt.cc/bbs/Gossiping/M.1583596761.A.A1C.html)

[0308 Kowdan：畜牲尼哥 要不要早點死一死](https://www.ptt.cc/bbs/Gossiping/M.1583633347.A.65F.html)

[0308 Merman19：垃圾尼哥等於間接害死歐美不知道多少人](https://www.ptt.cc/bbs/Gossiping/M.1583606672.A.944.html)

[0308 UDK0821：幹你娘智障尼哥](https://www.ptt.cc/bbs/Gossiping/M.1583670281.A.811.html)

[0308 bala73：尼哥水準](https://www.ptt.cc/bbs/Gossiping/M.1583649285.A.A51.html)

[0308 iamtan：捐到尼哥的私人帳戶嗎？](https://www.ptt.cc/bbs/Gossiping/M.1583598568.A.B2C.html)

[0308 jageillolin：尼哥從小窮困，現在被人民幣收買也是](https://www.ptt.cc/bbs/Gossiping/M.1583639012.A.DFF.html)

[0308 kuroro94：尼哥活該被當垃圾](https://www.ptt.cc/bbs/Gossiping/M.1583676026.A.611.html)

[0308 ufap：尼哥就是欠嗆](https://www.ptt.cc/bbs/Gossiping/M.1583641247.A.AE1.html)

[0309 WANGGGGGG：尼哥趁晚上偷爬到主席台 沒人發現](https://www.ptt.cc/bbs/Gossiping/M.1583751480.A.090.html)

[0309 dddc：非洲垃圾尼哥](https://www.ptt.cc/bbs/Gossiping/M.1583744877.A.D0B.html)

[0309 foralive520：尼哥的復仇](https://www.ptt.cc/bbs/Gossiping/M.1583725684.A.3F1.html)

[0309 hate56：尼哥:啊啊啊我又不小心要射惹阿](https://www.ptt.cc/bbs/Gossiping/M.1583742359.A.C7F.html)

[0309 modulation：尼哥被酸不是沒道理的](https://www.ptt.cc/bbs/Gossiping/M.1583759761.A.5DC.html)

[0310 ElsaKing：會被智障尼哥錯誤資訊騙 只會更糟](https://www.ptt.cc/bbs/Gossiping/M.1583814174.A.187.html)

[0310 f8954017：總結:cho=智障尼哥組織](https://www.ptt.cc/bbs/Gossiping/M.1583817134.A.46B.html)

[0310 peacenice：什麼尼哥支那野雞組織](https://www.ptt.cc/bbs/Gossiping/M.1583814481.A.74A.html)

[0310 yu800910：控你尼哥個頭](https://www.ptt.cc/bbs/Gossiping/M.1583792984.A.184.html)

[0310 zxc17893：WHO尼哥](https://www.ptt.cc/bbs/Gossiping/M.1583798836.A.F6E.html)

[0311 ayako0927：念在尼哥辛苦的種棉花 所以加分吧](https://www.ptt.cc/bbs/Gossiping/M.1583937478.A.48D.html)

[0311 hophers：尼哥是1  他名字都叫"彈到賽(台語)"了](https://www.ptt.cc/bbs/Gossiping/M.1583861616.A.F19.html)

[0311 hwsbetty：中共是原罪，更可惡的是尼哥。希望所有](https://www.ptt.cc/bbs/Gossiping/M.1583886005.A.E69.html)

[0311 overthinkin：尼哥快中標啊，不是要去中國醫治](https://www.ptt.cc/bbs/Gossiping/M.1583889584.A.80F.html)

[0311 phatman：尼哥：可是人民幣好香～](https://www.ptt.cc/bbs/Gossiping/M.1583893276.A.219.html)

[0312 Scubadive：幹您老師支那尼哥](https://www.ptt.cc/bbs/Gossiping/M.1583982839.A.4AB.html)

[0312 archie403：智障可悲尼哥](https://www.ptt.cc/bbs/Gossiping/M.1583977998.A.B17.html)

[0312 chaos0214：尼哥要把全世界都變成第三世界](https://www.ptt.cc/bbs/Gossiping/M.1583974501.A.F20.html)

[0312 cool911234：尼哥正在報復歐洲殖民](https://www.ptt.cc/bbs/Gossiping/M.1583970769.A.5B8.html)

[0312 doomhammer：尼哥你扛的起嗎?](https://www.ptt.cc/bbs/Gossiping/M.1583982836.A.2BF.html)

[0312 jeff0025：垃圾尼哥 都過幾個月了](https://www.ptt.cc/bbs/Gossiping/M.1583968516.A.FB4.html)

[0312 jeter17：尼哥好收買](https://www.ptt.cc/bbs/Gossiping/M.1584022850.A.068.html)

[0312 mekiael：草包尼哥 舔共組織](https://www.ptt.cc/bbs/Gossiping/M.1583993490.A.BF6.html)

[0312 nikewang：尼哥秘書長長的一臉公然猥褻臉](https://www.ptt.cc/bbs/Gossiping/M.1583949353.A.452.html)

[0312 qwe86295：垃圾支那尼哥](https://www.ptt.cc/bbs/Gossiping/M.1584007250.A.96C.html)

[0312 rabbit83035：cho尼哥：放任疫情的國家才失職](https://www.ptt.cc/bbs/Gossiping/M.1583980916.A.47A.html)

[0312 sarcasm111：智障尼哥](https://www.ptt.cc/bbs/Gossiping/M.1583965935.A.E82.html)

[0312 tigerface：白痴尼哥祝你得肺炎](https://www.ptt.cc/bbs/Gossiping/M.1583978112.A.8A7.html)

[0312 u9221036：尼哥](https://www.ptt.cc/bbs/Gossiping/M.1583987769.A.63D.html)

[0312 vking223：拉吉尼哥組織，史上最廢](https://www.ptt.cc/bbs/Gossiping/M.1583946144.A.D0A.html)

[0312 witnessg：沒人在乎你的看法，尼哥](https://www.ptt.cc/bbs/Gossiping/M.1583944715.A.DC7.html)

[0312 wwvvkai：你2月怎麼說的 垃圾尼哥](https://www.ptt.cc/bbs/Gossiping/M.1584021063.A.6B1.html)

[0312 yvonneXD：智障尼哥](https://www.ptt.cc/bbs/Gossiping/M.1584012938.A.4EE.html)

[0313 bcmaple：羨慕人家尼哥賺得比你多??](https://www.ptt.cc/bbs/Gossiping/M.1584065767.A.05F.html)

[0313 goldflower：喜聞樂見 希望尼哥塞害死自己家人](https://www.ptt.cc/bbs/Gossiping/M.1584100889.A.865.html)

[0313 lowlow1980：尼哥家人都去死吧](https://www.ptt.cc/bbs/Gossiping/M.1584103101.A.E27.html)

[0313 ohrring：這就是讓尼哥上臺的下場](https://www.ptt.cc/bbs/Gossiping/M.1584111461.A.23E.html)

[0313 samm3320：除了你養的尼哥以外誰給你正面評價了](https://www.ptt.cc/bbs/Gossiping/M.1584069332.A.AA4.html)

[0314 cloud1030：尼就是尼哥 只能種玉米跟跑步](https://www.ptt.cc/bbs/Gossiping/M.1584137848.A.4E3.html)

[0314 dddc：垃圾尼哥](https://www.ptt.cc/bbs/Gossiping/M.1584148368.A.D1B.html)

[0314 funnyrain：尼哥的復仇 用心良苦 歐美剉咧但](https://www.ptt.cc/bbs/Gossiping/M.1584152196.A.BD3.html)

[0314 jipq6175：因為有個垃圾尼哥跟他的習爹](https://www.ptt.cc/bbs/Gossiping/M.1584142277.A.B55.html)

[0314 kenyun：難怪中國要給每個尼哥留學生配三個女學伴](https://www.ptt.cc/bbs/Gossiping/M.1584118917.A.145.html)

[0314 misu2718：尼哥屌沒有每個都很大，黃先生](https://www.ptt.cc/bbs/Gossiping/M.1584162944.A.1B5.html)

[0314 pray：尼哥塞好有魄力喔 猛猛DER~](https://www.ptt.cc/bbs/Gossiping/M.1584122868.A.9C6.html)

[0314 sh1020112：笑死 這個尼哥眼裡只有錢](https://www.ptt.cc/bbs/Gossiping/M.1584197177.A.FA5.html)

[0314 yuyun0724：非洲那些尼哥國會死的最慘，活該相信支](https://www.ptt.cc/bbs/Gossiping/M.1584143803.A.AB4.html)

[0315 edoggiagia：垃圾尼哥](https://www.ptt.cc/bbs/Gossiping/M.1584202040.A.F5A.html)

[0315 goldenwave：尼哥有拿錢 就槍斃吧](https://www.ptt.cc/bbs/Gossiping/M.1584283092.A.72A.html)

[0315 grandwar：尼哥真的不演了呢，日本人最愛捐了去找](https://www.ptt.cc/bbs/Gossiping/M.1584287081.A.6BA.html)

[0315 jezz9740：尼哥就愛$](https://www.ptt.cc/bbs/Gossiping/M.1584240411.A.A13.html)

[0315 squallhung：尼哥滾](https://www.ptt.cc/bbs/Gossiping/M.1584230174.A.270.html)

[0316 a7860446：低能尼哥閉嘴啦垃圾！！](https://www.ptt.cc/bbs/Gossiping/M.1584322734.A.717.html)

[0316 andy00319：尼哥又摸麥的](https://www.ptt.cc/bbs/Gossiping/M.1584328194.A.6E2.html)

[0316 cytotoxic：尼哥家要燒起來了 尼哥老大還在洗手](https://www.ptt.cc/bbs/Gossiping/M.1584329594.A.E7F.html)

[0316 jaxjax：尼哥](https://www.ptt.cc/bbs/Gossiping/M.1584368663.A.6EC.html)

[0316 k70113：樓上有人在舔尼哥耶！尼哥真香 XD](https://www.ptt.cc/bbs/Gossiping/M.1584327427.A.F4E.html)

[0316 x7834210：尼哥舔中 歐美怠慢](https://www.ptt.cc/bbs/Gossiping/M.1584337898.A.8A5.html)

[0317 Boris945：什麼時候尼哥中啊](https://www.ptt.cc/bbs/Gossiping/M.1584442582.A.C67.html)

[0317 YilanRay：換另一個尼哥上任而已](https://www.ptt.cc/bbs/Gossiping/M.1584450626.A.2B9.html)

[0317 dddc：什麼時候處理who垃圾尼哥](https://www.ptt.cc/bbs/Gossiping/M.1584407881.A.C79.html)

[0317 leoqqqoel：尼哥](https://www.ptt.cc/bbs/Gossiping/M.1584445190.A.5F4.html)

[0317 marginal5566：換成別國腦袋就正常囉 垃圾尼哥](https://www.ptt.cc/bbs/Gossiping/M.1584406888.A.DEB.html)

[0317 usamigj：垃圾尼哥快集體CHO帶去中國燒一燒啊](https://www.ptt.cc/bbs/Gossiping/M.1584444605.A.A2B.html)

[0318 GaryOp：好了啦尼哥](https://www.ptt.cc/bbs/Gossiping/M.1584528466.A.524.html)

[0318 huabandd：進什麼WHO 看看低能尼哥](https://www.ptt.cc/bbs/Gossiping/M.1584502692.A.4B5.html)

[0318 pig19911118：支那尼哥一家親](https://www.ptt.cc/bbs/Gossiping/M.1584523572.A.E05.html)

[0318 wantshithole：尼哥who去死一死吧](https://www.ptt.cc/bbs/Gossiping/M.1584503043.A.018.html)

[0319 a0921387223：尼哥出來講啊 幹](https://www.ptt.cc/bbs/Gossiping/M.1584584771.A.7D3.html)

[0319 alexjeter：垃圾尼哥組織](https://www.ptt.cc/bbs/Gossiping/M.1584588449.A.0A5.html)

[0319 balius：尼哥有黑歷史也是很正常的XD](https://www.ptt.cc/bbs/Gossiping/M.1584604919.A.BD8.html)

[0319 dddc：尼哥垃圾就不要被清算](https://www.ptt.cc/bbs/Gossiping/M.1584614624.A.D90.html)

[0319 gogoro1314：尼哥出來打球！](https://www.ptt.cc/bbs/Gossiping/M.1584612442.A.56E.html)

[0319 henry55566：那位尼哥怎麼還沒被換下來太扯](https://www.ptt.cc/bbs/Gossiping/M.1584597972.A.F70.html)

[0319 innuendo3324：想到進去是那個尼哥做主就慘](https://www.ptt.cc/bbs/Gossiping/M.1584623345.A.587.html)

[0319 laechan：最近發現很多世界性組織頭子都是尼哥](https://www.ptt.cc/bbs/Gossiping/M.1584594791.A.7D8.html)

[0319 seies1989：操你媽黑人尼哥去死，廢物一個](https://www.ptt.cc/bbs/Gossiping/M.1584570161.A.A00.html)

[0320 ColinChu：抓到 尼哥台毒辣](https://www.ptt.cc/bbs/Gossiping/M.1584676552.A.D57.html)

[0320 Myramous：舌頭沾滿維尼屎的尼哥](https://www.ptt.cc/bbs/Gossiping/M.1584670710.A.7A4.html)

[0320 WOWO5566：舔支那的尼哥下台吧](https://www.ptt.cc/bbs/Gossiping/M.1584699889.A.F7D.html)

[0320 ohmama100：尼哥台獨份子](https://www.ptt.cc/bbs/Gossiping/M.1584691356.A.0D7.html)

[0320 serding：我都叫他雜種尼哥](https://www.ptt.cc/bbs/Gossiping/M.1584677235.A.D88.html)

[0320 taurus512：真他媽的垃圾尼哥](https://www.ptt.cc/bbs/Gossiping/M.1584664038.A.1F0.html)

[0320 tddt：尼哥又在跪舔中國爸爸](https://www.ptt.cc/bbs/Gossiping/M.1584682145.A.937.html)

[0320 winteryoyo：別相信支那尼哥](https://www.ptt.cc/bbs/Gossiping/M.1584679985.A.B39.html)

[0320 x7834210：尼哥很重要？？看看談屎得](https://www.ptt.cc/bbs/Gossiping/M.1584681616.A.480.html)

[0321 asdjjdsa：尼哥怎麼還沒確診？](https://www.ptt.cc/bbs/Gossiping/M.1584774523.A.4D2.html)

[0321 greg7575：死支那養的尼哥狗。王八蛋](https://www.ptt.cc/bbs/Gossiping/M.1584792169.A.94F.html)

[0321 howard878：去死吧智障尼哥](https://www.ptt.cc/bbs/Gossiping/M.1584802866.A.0A7.html)

[0321 light20735：尼哥去死](https://www.ptt.cc/bbs/Gossiping/M.1584745592.A.BA2.html)

[0322 gino0717：只有會開會的尼哥吧 那種組織](https://www.ptt.cc/bbs/Gossiping/M.1584888191.A.67A.html)

[0322 greensaru：尼哥博士](https://www.ptt.cc/bbs/Gossiping/M.1584851479.A.E80.html)

[0322 laba5566：一堆非洲尼哥還以為痰得屎是民族英雄](https://www.ptt.cc/bbs/Gossiping/M.1584848761.A.632.html)

[0323 Daz2005i：尼哥最需要準備的是腦](https://www.ptt.cc/bbs/Gossiping/M.1584939919.A.47D.html)

[0323 noname78531：有錢不一定有命花啊 垃圾尼哥 哪天被](https://www.ptt.cc/bbs/Gossiping/M.1584937285.A.85F.html)

[0324 Merman19：就那個垃圾尼哥阿，反人類罪啦](https://www.ptt.cc/bbs/Gossiping/M.1585029268.A.FB0.html)

[0324 airider：支那養的尼哥黑狗更可怕](https://www.ptt.cc/bbs/Gossiping/M.1585058652.A.108.html)

[0324 badguy227：尼哥當時正在用力舔沒空理你啦](https://www.ptt.cc/bbs/Gossiping/M.1585041241.A.B04.html)

[0324 bicedb：川普快派特種部隊去獵殺那個尼哥ㄅ](https://www.ptt.cc/bbs/Gossiping/M.1585062112.A.C92.html)

[0324 e49523：只有尼哥在肯定吧 公開透明好哦](https://www.ptt.cc/bbs/Gossiping/M.1585038430.A.183.html)

[0324 gunfighter：尼哥四肢發達智障種族 跟中國人絕配](https://www.ptt.cc/bbs/Gossiping/M.1585055974.A.D97.html)

[0324 kerry0496x：非洲尼哥的報仇](https://www.ptt.cc/bbs/Gossiping/M.1585063534.A.FB1.html)

[0324 mudee：尼哥被打臉  腫成豬頭了](https://www.ptt.cc/bbs/Gossiping/M.1585025788.A.4CB.html)

[0324 yoyo095235：幹就因為你垃圾尼哥還有在抽插你屁眼](https://www.ptt.cc/bbs/Gossiping/M.1585003320.A.32E.html)

[0325 airider：尼哥舔舔舔](https://www.ptt.cc/bbs/Gossiping/M.1585066845.A.E8D.html)

[0325 airider：支那養的尼哥狗很會舔](https://www.ptt.cc/bbs/Gossiping/M.1585148128.A.E12.html)

[0325 grafan：尼哥國衛生部長管世界的衛生？笑死人](https://www.ptt.cc/bbs/Gossiping/M.1585104171.A.336.html)

[0325 la8day：誰敢罵尼哥 等等告你歧視](https://www.ptt.cc/bbs/Gossiping/M.1585067664.A.4CC.html)

[0325 narutodante：尼哥](https://www.ptt.cc/bbs/Gossiping/M.1585101100.A.1D8.html)

[0325 rickphyman42：各國為了政治正確勉強讓尼哥帶頭](https://www.ptt.cc/bbs/Gossiping/M.1585109868.A.7EC.html)

[0325 timpotter：尼哥你的靈堂失火了，真讓人心碎](https://www.ptt.cc/bbs/Gossiping/M.1585097913.A.A2B.html)

[0326 JamesChan51：這個垃圾尼哥可以閉嘴嗎](https://www.ptt.cc/bbs/Gossiping/M.1585187182.A.8C9.html)

[0326 Lenney33：尼哥表示喜悅](https://www.ptt.cc/bbs/Gossiping/M.1585237992.A.E53.html)

[0326 asole：給錢就唸稿子的尼哥](https://www.ptt.cc/bbs/Gossiping/M.1585184133.A.7D1.html)

[0326 fernand：尼哥，你現在能做的就是下台，讓一個不會](https://www.ptt.cc/bbs/Gossiping/M.1585203498.A.F39.html)

[0326 highyes：垃圾尼哥國  斷一斷啦！](https://www.ptt.cc/bbs/Gossiping/M.1585224480.A.320.html)

[0326 jonaswang01：尼哥本能到處舔](https://www.ptt.cc/bbs/Gossiping/M.1585177505.A.BB6.html)

[0326 revorea：尼哥之恥](https://www.ptt.cc/bbs/Gossiping/M.1585183601.A.34B.html)

[0326 seedage：精神錯亂垃圾尼哥](https://www.ptt.cc/bbs/Gossiping/M.1585236030.A.A02.html)

[0326 swgun：尼哥只要有錢他老爸的屁眼都能給你幹](https://www.ptt.cc/bbs/Gossiping/M.1585219596.A.642.html)

[0327 Renaud：尼哥的肛塞會自動定位：位置—北京](https://www.ptt.cc/bbs/Gossiping/M.1585275762.A.49F.html)

[0327 a229353：尼哥回家跟維尼爸爸哭啊](https://www.ptt.cc/bbs/Gossiping/M.1585271281.A.525.html)

[0327 allmygod：低能尼哥 你再講一次我撕爛你的嘴](https://www.ptt.cc/bbs/Gossiping/M.1585264560.A.07F.html)

[0327 aoilan：網軍在前幾樓帶風向很忙的  尼哥不要吵](https://www.ptt.cc/bbs/Gossiping/M.1585262490.A.151.html)

[0327 baliallin：台灣動員的話會只有50幾萬?白癡尼哥](https://www.ptt.cc/bbs/Gossiping/M.1585274739.A.CD2.html)

[0327 baliallin：由無恥支那、貪汙尼哥、智障白左組成](https://www.ptt.cc/bbs/Gossiping/M.1585299071.A.F8F.html)

[0327 gatsbyhsu：垃圾尼哥還有臉嘴台灣](https://www.ptt.cc/bbs/Gossiping/M.1585264156.A.9DD.html)

[0327 gz：低能尼哥 關台灣屁事](https://www.ptt.cc/bbs/Gossiping/M.1585305473.A.4AF.html)

[0327 sc85508：非洲尼哥水準](https://www.ptt.cc/bbs/Gossiping/M.1585315750.A.27F.html)

[0327 slovea：支那豬加上尼哥足以毀滅全世界](https://www.ptt.cc/bbs/Gossiping/M.1585280986.A.C3A.html)

[0327 whitenoise：尼哥應該去唱RAP](https://www.ptt.cc/bbs/Gossiping/M.1585283450.A.F9C.html)

[0327 wtmjs：垃圾尼哥](https://www.ptt.cc/bbs/Gossiping/M.1585273928.A.3F9.html)

[0327 x7834210：尼哥垃圾不意外](https://www.ptt.cc/bbs/Gossiping/M.1585309474.A.6B3.html)

[0327 yuyun0724：這些尼哥跟支那人一起死吧](https://www.ptt.cc/bbs/Gossiping/M.1585266094.A.DDF.html)

[0328 Googletime：黑鬼尼哥](https://www.ptt.cc/bbs/Gossiping/M.1585393340.A.294.html)

[0328 fenix220：有支那尼哥在](https://www.ptt.cc/bbs/Gossiping/M.1585410552.A.708.html)

[0328 gino0717：尼哥只會表演洗手](https://www.ptt.cc/bbs/Gossiping/M.1585410467.A.041.html)

[0328 popopal：連CHO尼哥都在蹭台灣了](https://www.ptt.cc/bbs/Gossiping/M.1585325693.A.CF5.html)

[0328 specialcat1：造謠尼哥](https://www.ptt.cc/bbs/Gossiping/M.1585379674.A.11C.html)

[0328 stlevi811101：不只痰德賽那個尼哥 風險主管 整個組織都是這副鳥樣](https://www.ptt.cc/bbs/Gossiping/M.1585396524.A.7DC.html)

[0329 foolfighter：尼哥滾](https://www.ptt.cc/bbs/Gossiping/M.1585486754.A.9CA.html)

[0329 gatsbyhsu：尼哥舔共抱腿](https://www.ptt.cc/bbs/Gossiping/M.1585412011.A.EFD.html)

[0330 HwaSIn：那個垃圾尼哥還有加拿大white trash什麼時候要滾](https://www.ptt.cc/bbs/Gossiping/M.1585568843.A.049.html)

[0330 bubbleking：尼哥下台我才信](https://www.ptt.cc/bbs/Gossiping/M.1585565474.A.6BF.html)

[0330 togmogo：跟沒屁用的尼哥通話](https://www.ptt.cc/bbs/Gossiping/M.1585550567.A.1CF.html)

[0331 dream1124：台灣幹麻浪費力氣跟中國和尼哥搞政治程序的推推拉拉？](https://www.ptt.cc/bbs/Gossiping/M.1585612993.A.25D.html)

[0331 frankykick：北京養的尼哥狗](https://www.ptt.cc/bbs/Gossiping/M.1585615414.A.AE1.html)

[0331 getwild：這垃圾收的黑錢應該僅此於尼哥](https://www.ptt.cc/bbs/Gossiping/M.1585626836.A.E9E.html)

[0331 kixer2005：吃屎啦  你們呼呼嘿嘿狗屎尼哥組織自己去玩](https://www.ptt.cc/bbs/Gossiping/M.1585625063.A.ED3.html)

[0401 DASHOCK：看到gm是黑心尼哥就跳了](https://www.ptt.cc/bbs/Gossiping/M.1585752875.A.B85.html)

[0401 hc23：黑奴尼哥](https://www.ptt.cc/bbs/Gossiping/M.1585739489.A.822.html)

[0401 jeffkent：查支那尼哥就夠](https://www.ptt.cc/bbs/Gossiping/M.1585732645.A.F2E.html)

[0401 koushimei：幹你鳥的尼哥](https://www.ptt.cc/bbs/Gossiping/M.1585725530.A.19E.html)

[0401 rosydark：貪婪尼哥，跟超級盤子](https://www.ptt.cc/bbs/Gossiping/M.1585753211.A.330.html)

[0401 zxzzzzzzzzzz：譚屎尼哥中國養的狗](https://www.ptt.cc/bbs/Gossiping/M.1585755437.A.34C.html)

[0402 peter5140：要讓台灣當WHO老大啦，誰需要垃圾尼哥](https://www.ptt.cc/bbs/Gossiping/M.1585817582.A.95E.html)

[0402 sheepmeamea：尼哥是在擔憂自己被究責吧](https://www.ptt.cc/bbs/Gossiping/M.1585801928.A.B6F.html)

[0402 smallplug：這就是為什麼不能讓尼哥掌權](https://www.ptt.cc/bbs/Gossiping/M.1585787221.A.4EC.html)

[0402 snow3804：尼哥閉嘴](https://www.ptt.cc/bbs/Gossiping/M.1585787935.A.CC8.html)

[0404 jezz9740：垃圾尼哥帶著你的垃圾組織去跳海吧](https://www.ptt.cc/bbs/Gossiping/M.1586003040.A.5E7.html)

[0404 laba5566：還不吊死談淂賽那個尼哥 美國智障](https://www.ptt.cc/bbs/Gossiping/M.1585937639.A.AAE.html)

[0404 lmf770410：尼哥就收錢辦事啊](https://www.ptt.cc/bbs/Gossiping/M.1585987664.A.DEE.html)

[0404 morichi：活該阿 還讓尼哥當會長 死好](https://www.ptt.cc/bbs/Gossiping/M.1585939999.A.D0F.html)

[0404 popopal：自己去參加垃圾尼哥的組織吧 除非換老美為首](https://www.ptt.cc/bbs/Gossiping/M.1585972275.A.30B.html)

[0405 touchbird：最好衣索比亞的尼哥是專家啦](https://www.ptt.cc/bbs/Gossiping/M.1586059219.A.CB6.html)

[0406 slovea：尼哥+支那就夠噓了好嗎](https://www.ptt.cc/bbs/Gossiping/M.1586147221.A.D33.html)

[0407 DDJwolf：操妳媽，幹話尼哥](https://www.ptt.cc/bbs/Gossiping/M.1586211695.A.37B.html)

[0407 FuYunlol：尼哥也懂震怒？](https://www.ptt.cc/bbs/Gossiping/M.1586264724.A.6C4.html)

[0408 AFISH111：他是有差逆   垃圾尼哥早就舔中國舔飽了  了不起不做](https://www.ptt.cc/bbs/Gossiping/M.1586332534.A.C3B.html)

[0408 AMDMARSHAL：垃圾尼哥 幹](https://www.ptt.cc/bbs/Gossiping/M.1586358640.A.AF7.html)

[0408 BaGaJohn5566：尼哥就中國傀儡啊 他講的態度都是中共態度](https://www.ptt.cc/bbs/Gossiping/M.1586361049.A.568.html)

[0408 JamesChan51：爽啦，垃圾尼哥再舔支那啊](https://www.ptt.cc/bbs/Gossiping/M.1586348116.A.483.html)

[0408 Segal：米國老爸：我左手空出來了，尼哥你死定了](https://www.ptt.cc/bbs/Gossiping/M.1586276100.A.0E9.html)

[0408 arrenwu：這問題不是尼哥 誰挺尼哥](https://www.ptt.cc/bbs/Gossiping/M.1586323776.A.DCA.html)

[0408 fish0713：中國已經在非洲灑很多錢了，反正廢物低智商尼哥用錢收買](https://www.ptt.cc/bbs/Gossiping/M.1586302051.A.0AF.html)

[0408 grandwar：當初就是尼哥才被迫退出的，早就不意外。歐美仔現在就跟](https://www.ptt.cc/bbs/Gossiping/M.1586310695.A.16D.html)

[0408 naruto611216：尼哥](https://www.ptt.cc/bbs/Gossiping/M.1586341087.A.ED3.html)

[0408 nineuniverse：那些尼哥和國家都有收賄啊](https://www.ptt.cc/bbs/Gossiping/M.1586276617.A.23F.html)

[0408 pulesiya：再塞個幾倍的錢到尼哥口袋說不定可](https://www.ptt.cc/bbs/Gossiping/M.1586313496.A.043.html)

[0409 AIdrawer：垃圾尼哥](https://www.ptt.cc/bbs/Gossiping/M.1586395963.A.A85.html)

[0409 CenaC：但是的確歧視啊 你搜尋一下尼哥就一堆推文了](https://www.ptt.cc/bbs/Gossiping/M.1586407462.A.56B.html)

[0409 DrDisk：尼哥自慚形穢](https://www.ptt.cc/bbs/Gossiping/M.1586414596.A.37F.html)

[0409 EIngXuan：支那尼哥又不是衣國](https://www.ptt.cc/bbs/Gossiping/M.1586431689.A.C6F.html)

[0409 FakeGPS：是被尼哥攻佔了吧 譚德賽使用種族騎士之術召喚出來的](https://www.ptt.cc/bbs/Gossiping/M.1586385603.A.D50.html)

[0409 Sam0453：只要是黑人，在臺灣容易被說是尼哥](https://www.ptt.cc/bbs/Gossiping/M.1586443517.A.C92.html)

[0409 Seifer601：爽啊 罵到尼哥7pupu](https://www.ptt.cc/bbs/Gossiping/M.1586402270.A.BC7.html)

[0409 VIATOR：尼哥本來就是很不尊敬的叫法了，本來就不該那樣稱呼了](https://www.ptt.cc/bbs/Gossiping/M.1586411187.A.632.html)

[0409 VOLK11：尼哥要森七七，那是他的自由](https://www.ptt.cc/bbs/Gossiping/M.1586373483.A.62E.html)

[0409 ViktorGoogle：尼哥](https://www.ptt.cc/bbs/Gossiping/M.1586406078.A.B66.html)

[0409 Wall62：中國養的白痴尼哥](https://www.ptt.cc/bbs/Gossiping/M.1586379386.A.4A1.html)

[0409 Wall62：中國養的白痴尼哥](https://www.ptt.cc/bbs/Gossiping/M.1586385809.A.41B.html)

[0409 Wall62：中國養的白痴尼哥](https://www.ptt.cc/bbs/Gossiping/M.1586395357.A.15D.html)

[0409 Wall62：中國養的白痴尼哥](https://www.ptt.cc/bbs/Gossiping/M.1586415948.A.47B.html)

[0409 Yginger1：尼哥](https://www.ptt.cc/bbs/Gossiping/M.1586388370.A.C95.html)

[0409 a0921387223：整天跳版欸 尼哥](https://www.ptt.cc/bbs/Gossiping/M.1586405300.A.2CE.html)

[0409 a1919979：講他尼哥還污辱尼哥這個詞好嗎？](https://www.ptt.cc/bbs/Gossiping/M.1586393510.A.75D.html)

[0409 ai2311：台灣人不用尼哥罵人？看來你還是不了解台灣人](https://www.ptt.cc/bbs/Gossiping/M.1586435075.A.E43.html)

[0409 appletofu：我狹窄怎麼了嗎尼哥](https://www.ptt.cc/bbs/Gossiping/M.1586388726.A.73E.html)

[0409 armorblocks：尼哥](https://www.ptt.cc/bbs/Gossiping/M.1586446091.A.885.html)

[0409 belucky：這垃圾尼哥只會被自殺      不可能自殺](https://www.ptt.cc/bbs/Gossiping/M.1586414221.A.7FD.html)

[0409 bigtien6292：尼哥含屎噴人 回家吃蒼蠅肉餅](https://www.ptt.cc/bbs/Gossiping/M.1586390771.A.112.html)

[0409 bluu：中國太監的尼哥 把大黑屌割掉只為了人民幣的尼哥](https://www.ptt.cc/bbs/Gossiping/M.1586405618.A.D87.html)

[0409 bob120400：尼哥 假賽](https://www.ptt.cc/bbs/Gossiping/M.1586404132.A.BC4.html)

[0409 c24253994：垃圾尼哥](https://www.ptt.cc/bbs/Gossiping/M.1586406883.A.78F.html)

[0409 citizen5566：五樓尼哥蓋](https://www.ptt.cc/bbs/Gossiping/M.1586405895.A.8F2.html)

[0409 color3258：尼哥中國一家親 難怪愛滋都超多 嘔嘔嘔嘔嘔嘔嘔嘔](https://www.ptt.cc/bbs/Gossiping/M.1586404450.A.C68.html)

[0409 cool911234：馬尼哥逼](https://www.ptt.cc/bbs/Gossiping/M.1586427768.A.14B.html)

[0409 cul287：白蟑螂尼哥也吃 ㄏㄏ](https://www.ptt.cc/bbs/Gossiping/M.1586402091.A.D2C.html)

[0409 cxiop：好，支那尼哥犬](https://www.ptt.cc/bbs/Gossiping/M.1586426846.A.78D.html)

[0409 ferrisw：垃圾尼哥](https://www.ptt.cc/bbs/Gossiping/M.1586376381.A.33A.html)

[0409 ilovebmw：尼哥玻璃心](https://www.ptt.cc/bbs/Gossiping/M.1586371712.A.94E.html)

[0409 jakeblue：尼哥](https://www.ptt.cc/bbs/Gossiping/M.1586444776.A.7A8.html)

[0409 jezz9740：尼哥: 台灣在國外的網軍](https://www.ptt.cc/bbs/Gossiping/M.1586400498.A.293.html)

[0409 jorden：好的 尼哥](https://www.ptt.cc/bbs/Gossiping/M.1586422369.A.BA8.html)

[0409 jorden：尼哥死要錢啦 去非洲就知道 只會money money](https://www.ptt.cc/bbs/Gossiping/M.1586421967.A.48A.html)

[0409 kevin05233：...根本沒人鳥那隻尼哥亂吠好嗎......](https://www.ptt.cc/bbs/Gossiping/M.1586440142.A.DE9.html)

[0409 killer922：尼哥聽到不給錢先生77，然後再去找習大大哭哭](https://www.ptt.cc/bbs/Gossiping/M.1586389294.A.EA0.html)

[0409 klagalas：垃圾尼哥閉嘴](https://www.ptt.cc/bbs/Gossiping/M.1586407180.A.C69.html)

[0409 knik119：尼哥對增加台灣曝光度，其實大大有貢獻](https://www.ptt.cc/bbs/Gossiping/M.1586368362.A.CDA.html)

[0409 kt9701：尼哥明示"台灣不是中國的"](https://www.ptt.cc/bbs/Gossiping/M.1586424062.A.F8D.html)

[0409 lanlance：尼哥](https://www.ptt.cc/bbs/Gossiping/M.1586432012.A.6FF.html)

[0409 limyeeshin：網軍人多手雜 不小心寫了些尼哥之類的文字也是很正常](https://www.ptt.cc/bbs/Gossiping/M.1586447943.A.0B1.html)

[0409 lulumielu：尼哥是歧視？](https://www.ptt.cc/bbs/Gossiping/M.1586392180.A.D8A.html)

[0409 magiteemo：回操你媽垃圾尼哥就對了 爽歪歪](https://www.ptt.cc/bbs/Gossiping/M.1586376325.A.5AF.html)

[0409 maplefff：滿意了！ 黑人尼哥去譚裡面爽](https://www.ptt.cc/bbs/Gossiping/M.1586445593.A.C39.html)

[0409 modulation：尼哥的主人](https://www.ptt.cc/bbs/Gossiping/M.1586434773.A.21D.html)

[0409 ny40yankees：垃圾尼哥就是垃圾](https://www.ptt.cc/bbs/Gossiping/M.1586395011.A.02B.html)

[0409 phyBomber：換了一個尼哥還有千千萬萬個尼哥](https://www.ptt.cc/bbs/Gossiping/M.1586399902.A.972.html)

[0409 pian0214：真的 韓國論壇也不太在乎尼哥被罵 反而也一起罵尼哥 黑](https://www.ptt.cc/bbs/Gossiping/M.1586444638.A.66C.html)

[0409 pony0411：英美重新組一個團體不就好了，中國的尼哥掰掰](https://www.ptt.cc/bbs/Gossiping/M.1586393165.A.B16.html)

[0409 popopal：恩阿　再幫台灣打知名度　尼哥也算IQ低　中台灣網軍招了](https://www.ptt.cc/bbs/Gossiping/M.1586441332.A.A57.html)

[0409 rahim03：柯粉要崩潰了 不久前才在亂抓罵尼哥的](https://www.ptt.cc/bbs/Gossiping/M.1586430667.A.B26.html)

[0409 rodney92：舔共豪是尼哥人 別吵](https://www.ptt.cc/bbs/Gossiping/M.1586402337.A.1FF.html)

[0409 rosydark：支那賤畜養的尼哥狗，不意外](https://www.ptt.cc/bbs/Gossiping/M.1586447160.A.FF9.html)

[0409 ryan0222：逞口舌之快，嘴尼哥種族歧視落人口實，結果作白工](https://www.ptt.cc/bbs/Gossiping/M.1586443265.A.3BC.html)

[0409 sai0613：\尼哥/ \支那狗/ \尼哥/ \支那狗/ \尼哥/ \支那狗/](https://www.ptt.cc/bbs/Gossiping/M.1586412392.A.EB6.html)

[0409 sam30292002：尼哥大聯盟](https://www.ptt.cc/bbs/Gossiping/M.1586403344.A.D08.html)

[0409 smallplug：尼哥去種棉花啦](https://www.ptt.cc/bbs/Gossiping/M.1586403056.A.43D.html)

[0409 smallplug：尼哥哈哈尼哥](https://www.ptt.cc/bbs/Gossiping/M.1586407777.A.E97.html)

[0409 smallz：尼哥去死](https://www.ptt.cc/bbs/Gossiping/M.1586403373.A.BD9.html)

[0409 stephenliu：垃圾尼哥 去跪舔習近平老二吧 最好連懶趴也一起吞進去](https://www.ptt.cc/bbs/Gossiping/M.1586404902.A.986.html)

[0409 theclgy2001：你知道非洲尼哥比較愛未成年新疆處女嗎](https://www.ptt.cc/bbs/Gossiping/M.1586405396.A.02A.html)

[0409 timpotter：做賊喊抓賊，這個尼哥沒有下限](https://www.ptt.cc/bbs/Gossiping/M.1586386763.A.552.html)

[0409 toorger：好的，尼哥](https://www.ptt.cc/bbs/Gossiping/M.1586374823.A.F83.html)

[0409 toorger：好的，尼哥大團結](https://www.ptt.cc/bbs/Gossiping/M.1586397624.A.91D.html)

[0409 tp6m4g0：尼哥negro單純指黑人，沒有貶義](https://www.ptt.cc/bbs/Gossiping/M.1586445869.A.3A2.html)

[0409 victoryss：每天上PTT  看綠色蟑螂演猴戲  夜夜尼哥](https://www.ptt.cc/bbs/Gossiping/M.1586446135.A.62B.html)

[0409 waverson：尼哥滾回家種棉花](https://www.ptt.cc/bbs/Gossiping/M.1586405317.A.A29.html)

[0409 white930：尼哥哭哭](https://www.ptt.cc/bbs/Gossiping/M.1586393875.A.629.html)

[0409 widec：尼哥之恥  只會舔習維尼的懶趴](https://www.ptt.cc/bbs/Gossiping/M.1586395242.A.F3F.html)

[0409 widec：我啦 是我罵譚德塞尼哥的啦 叫譚德塞來找我阿幹](https://www.ptt.cc/bbs/Gossiping/M.1586419407.A.298.html)

[0409 yaoyuuichi：尼哥滾啦www](https://www.ptt.cc/bbs/Gossiping/M.1586370402.A.2F4.html)

[0409 zxsx811：中共稿子 尼哥照稿念](https://www.ptt.cc/bbs/Gossiping/M.1586409525.A.34F.html)

[0410 ARCHER2234：支那尼哥，我還是照講，叫牠咬我啊](https://www.ptt.cc/bbs/Gossiping/M.1586496254.A.AA2.html)

[0410 ARCHER2234：等等，可是我也有罵尼哥呦](https://www.ptt.cc/bbs/Gossiping/M.1586498778.A.F35.html)

[0410 Behind4：台灣幹嘛加入尼哥組織?](https://www.ptt.cc/bbs/Gossiping/M.1586525844.A.DB2.html)

[0410 KA：幹 罵不罵都進不去 為什麼不罵 草泥馬垃圾尼哥](https://www.ptt.cc/bbs/Gossiping/M.1586525362.A.846.html)

[0410 Rin5566：吃屎吧 譚德塞尼哥](https://www.ptt.cc/bbs/Gossiping/M.1586517323.A.DB8.html)

[0410 Scott850205：中時也都尼哥](https://www.ptt.cc/bbs/Gossiping/M.1586476154.A.299.html)

[0410 Y2KGreentea：尼哥在演什麼？](https://www.ptt.cc/bbs/Gossiping/M.1586487500.A.63C.html)

[0410 amgn997：刊登尼哥去死，台灣藍波萬](https://www.ptt.cc/bbs/Gossiping/M.1586500850.A.75A.html)

[0410 castjane：尼哥這詞台灣以前沒出現](https://www.ptt.cc/bbs/Gossiping/M.1586480490.A.C7E.html)

[0410 cca1109：智障柯糞又想甩鍋 不知道誰昨天造謠尼哥是粉專講的跟譚一](https://www.ptt.cc/bbs/Gossiping/M.1586534093.A.C27.html)

[0410 cli6012：尼哥就尼哥 做那麼爛 還不下台 比韓總機還不如](https://www.ptt.cc/bbs/Gossiping/M.1586532607.A.99B.html)

[0410 cocaineweed：看看台灣的錢多還是尼哥的鑽石多](https://www.ptt.cc/bbs/Gossiping/M.1586527943.A.0CB.html)

[0410 dyrus：尼哥聯盟](https://www.ptt.cc/bbs/Gossiping/M.1586484884.A.C3D.html)

[0410 elec1141：尼哥窟](https://www.ptt.cc/bbs/Gossiping/M.1586529735.A.61C.html)

[0410 friends29：支那賤畜不意外 非洲尼哥自導自演](https://www.ptt.cc/bbs/Gossiping/M.1586488709.A.8FC.html)

[0410 funnyrain：三個月前網軍1450都在罵韓國瑜誰有空理你這個尼哥啊](https://www.ptt.cc/bbs/Gossiping/M.1586493213.A.5D7.html)

[0410 hhh770509：好的 尼哥痰德賽](https://www.ptt.cc/bbs/Gossiping/M.1586448753.A.B44.html)

[0410 iamdota：尼哥師傅柯糞炳忠爭舔維尼哥屌  維尼哥屌真香](https://www.ptt.cc/bbs/Gossiping/M.1586484409.A.9DA.html)

[0410 iamdota：爽　看愛支柯痰粉崩潰就精神特別好　尼哥舔維尼哥屌](https://www.ptt.cc/bbs/Gossiping/M.1586483039.A.5C5.html)

[0410 jeff21115：尼哥是negro還是nigger 的音譯?](https://www.ptt.cc/bbs/Gossiping/M.1586503311.A.C7F.html)

[0410 kom8989：五毛賤畜跟痰尼哥一搭一唱](https://www.ptt.cc/bbs/Gossiping/M.1586529672.A.5B8.html)

[0410 linhsiuwei：樓下支援尼哥抬棺.gif](https://www.ptt.cc/bbs/Gossiping/M.1586527581.A.6B5.html)

[0410 niburger1001：尼哥](https://www.ptt.cc/bbs/Gossiping/M.1586514518.A.85C.html)

[0410 rockon15：尼哥 賤畜1450死全家 早點火葬](https://www.ptt.cc/bbs/Gossiping/M.1586497883.A.458.html)

[0410 s7385246：尼哥就是尼哥 就像天安門一樣啊 有問題啊XD?](https://www.ptt.cc/bbs/Gossiping/M.1586462708.A.D12.html)

[0410 sameday：尼哥又要哭了](https://www.ptt.cc/bbs/Gossiping/M.1586487442.A.4D4.html)

[0410 sarcasm111：維尼與尼哥連技 簡稱維尼哥連技](https://www.ptt.cc/bbs/Gossiping/M.1586451182.A.15B.html)

[0410 tp6m4g0：尼哥(negro)單純指黑色人種，沒負面意思](https://www.ptt.cc/bbs/Gossiping/M.1586482546.A.69B.html)

[0410 tp6m4g0：尼哥(negro)單純指黑色人種，沒負面意思](https://www.ptt.cc/bbs/Gossiping/M.1586483025.A.1EC.html)

[0410 x7834210：媽的支那賤畜配合尼哥譚得屎演戲](https://www.ptt.cc/bbs/Gossiping/M.1586475530.A.990.html)

[0410 xxhsuval：黑人尼哥](https://www.ptt.cc/bbs/Gossiping/M.1586450892.A.84D.html)

[0410 yyyyyyyv：因為現在一堆支那人是非洲尼哥幹出來的](https://www.ptt.cc/bbs/Gossiping/M.1586454212.A.38C.html)

[0410 zagato：我出10元徵求狂甲去肛爆那個尼哥](https://www.ptt.cc/bbs/Gossiping/M.1586493886.A.92A.html)

[0410 zxc17893：尼哥抬棺==](https://www.ptt.cc/bbs/Gossiping/M.1586502864.A.EC1.html)

[0411 Agent5566：五毛花錢叫非洲小孩唸尼哥比較厲害](https://www.ptt.cc/bbs/Gossiping/M.1586574909.A.6F9.html)

[0411 AioTakumi：可以不要74尼哥嗎？](https://www.ptt.cc/bbs/Gossiping/M.1586560501.A.C23.html)

[0411 Behind4：你把尼哥放在哪裡了?](https://www.ptt.cc/bbs/Gossiping/M.1586570211.A.91F.html)

[0411 VOLK11：尼哥是以前就講了，是暱稱](https://www.ptt.cc/bbs/Gossiping/M.1586539629.A.CCA.html)

[0411 a6444long：你會為了尼哥打戰嘛？](https://www.ptt.cc/bbs/Gossiping/M.1586575882.A.A43.html)

[0411 aprilsheep：去這個組織，又要被騙錢養中共的尼哥，不去省錢清爽](https://www.ptt.cc/bbs/Gossiping/M.1586560886.A.130.html)

[0411 awenracious：不要高估尼哥的智商，你不給他指令他就不會做事了，](https://www.ptt.cc/bbs/Gossiping/M.1586548309.A.3E8.html)

[0411 coolknight：不是以自己是尼哥為驕傲嗎？](https://www.ptt.cc/bbs/Gossiping/M.1586560340.A.B47.html)

[0411 fedona：支那尼哥又被打臉了](https://www.ptt.cc/bbs/Gossiping/M.1586579907.A.1F4.html)

[0411 maiarim：我們超有言論自由啊 所以你看現在PTT「尼哥」的截圖在推](https://www.ptt.cc/bbs/Gossiping/M.1586605687.A.0A8.html)

[0411 pulesiya：沒辦法把尼哥拔掉嗎](https://www.ptt.cc/bbs/Gossiping/M.1586572292.A.FDE.html)

[0411 seraphic298：智障尼哥 這麼好被打臉的謊也要撒](https://www.ptt.cc/bbs/Gossiping/M.1586585582.A.873.html)

[0411 steven0503：人太垃圾 不然誰想說你尼哥 幹你娘](https://www.ptt.cc/bbs/Gossiping/M.1586569149.A.4CC.html)

[0411 wadadihaga：信裡面怎麼沒講到尼哥？](https://www.ptt.cc/bbs/Gossiping/M.1586572256.A.8C6.html)

[0411 xzcb2008：畜生黑人尼哥東西就是髒](https://www.ptt.cc/bbs/Gossiping/M.1586582449.A.84D.html)

[0412 Boris945：那個可憐啊垃圾尼哥應該是台灣人沒錯吧](https://www.ptt.cc/bbs/Gossiping/M.1586658431.A.EB2.html)

[0412 Informatik：那早就被白種人噴爆了，就是因為他是尼哥白人才不敢噴](https://www.ptt.cc/bbs/Gossiping/M.1586659913.A.8BD.html)

[0412 XXXXSOW：操你媽乞丐尼哥 智障強森死得不冤 安心上路吧](https://www.ptt.cc/bbs/Gossiping/M.1586684330.A.463.html)

[0412 excercang：尼哥有收錢阿，只能當中國的狗](https://www.ptt.cc/bbs/Gossiping/M.1586683437.A.FF4.html)

[0412 handsomeKim：舔共匪的尼哥狗](https://www.ptt.cc/bbs/Gossiping/M.1586665766.A.E64.html)

[0412 jameswen：死要錢垃圾尼哥，不做事只看錢](https://www.ptt.cc/bbs/Gossiping/M.1586623644.A.D3B.html)

[0413 Benbenyale：貪婪尼哥](https://www.ptt.cc/bbs/Gossiping/M.1586785070.A.FA7.html)

[0413 GGrunrundela：你吧肏 噁爛死盼子五毛ㄈㄓ尼哥嘔嘔嘔嘔嘔幹幹幹幹](https://www.ptt.cc/bbs/Gossiping/M.1586742634.A.4CE.html)

[0413 Mrgoat：上面就一堆尼哥推文了，哪裡沒有種族歧視？](https://www.ptt.cc/bbs/Gossiping/M.1586752842.A.632.html)

[0413 geesegeese：別侮辱尼哥，潭是中國人，非洲之恥](https://www.ptt.cc/bbs/Gossiping/M.1586751854.A.056.html)

[0413 sakula0616：說他是尼哥怎麼了?  我還罵他是垃圾  我呸](https://www.ptt.cc/bbs/Gossiping/M.1586745891.A.1F7.html)

[0413 uminoko：等等尼哥看到PTT又會說台灣攻擊他嘻嘻](https://www.ptt.cc/bbs/Gossiping/M.1586780360.A.0C8.html)

[0413 vi000246：垃圾尼哥 來查我啊](https://www.ptt.cc/bbs/Gossiping/M.1586748488.A.E13.html)

[0414 c7683fh6：尼哥怕了？](https://www.ptt.cc/bbs/Gossiping/M.1586830480.A.0B0.html)

[0414 freddy8317：賤種尼哥 皮膚跟良心一樣歐罵馬](https://www.ptt.cc/bbs/Gossiping/M.1586845746.A.776.html)

[0414 homerunball：尼哥出頭很多](https://www.ptt.cc/bbs/Gossiping/M.1586828923.A.FB0.html)

[0414 markkao456：殺人魔下台啦王八尼哥](https://www.ptt.cc/bbs/Gossiping/M.1586817919.A.F0E.html)

[0414 prkfcpr：連台灣人自己都不團結，難怪被尼哥看不起](https://www.ptt.cc/bbs/Gossiping/M.1586819210.A.815.html)

[0414 whacker：支那不如尼哥](https://www.ptt.cc/bbs/Gossiping/M.1586852631.A.591.html)
