長庚大學 大數據分析方法 作業三
================

網站資料爬取
------------

``` r
library(rvest) 
```

    ## Loading required package: xml2

``` r
PTT<-"https://www.ptt.cc/bbs/NBA/index4628.html"
PTTContent<-read_html(PTT)
post_title <- PTTContent %>% html_nodes(".title") %>% html_text() 
post_title
```

    ##  [1] "\n\t\t\t\n\t\t\t\t[BOX ] Nuggets 113:122 Blazers 數據\n\t\t\t\n\t\t\t"          
    ##  [2] "\n\t\t\t\n\t\t\t\t[BOX ] Wizards 119:108 Lakers 數據\n\t\t\t\n\t\t\t"           
    ##  [3] "\n\t\t\t\n\t\t\t\tRe: [新聞] 林書豪在場能量加倍 籃網輸球也精彩\n\t\t\t\n\t\t\t" 
    ##  [4] "\n\t\t\t\n\t\t\t\tRe: [討論] NBA球員有拿過大滿貫的?\n\t\t\t\n\t\t\t"            
    ##  [5] "\n\t\t\t\n\t\t\t\tRe: [討論] 留KD或Curry？\n\t\t\t\n\t\t\t"                     
    ##  [6] "\n\t\t\t\n\t\t\t\t[情報] ESPN:馬刺4：0擊敗去年東西冠軍\n\t\t\t\n\t\t\t"         
    ##  [7] "\n\t\t\t\n\t\t\t\t[新聞] 諾克奇33分轟前東家金塊　拓荒者老8之爭\n\t\t\t\n\t\t\t" 
    ##  [8] "\n\t\t\t\n\t\t\t\t[情報] NBA Standings(2017.03.29)\n\t\t\t\n\t\t\t"             
    ##  [9] "\n\t\t\t\n\t\t\t\t[公告] NBA 板 開始舉辦樂透!\n\t\t\t\n\t\t\t"                  
    ## [10] "\n\t\t\t\n\t\t\t\t[外絮] Is it time to sit James Harden?\n\t\t\t\n\t\t\t"       
    ## [11] "\n\t\t\t\n\t\t\t\t[新聞] 史上第一人！哈登總得分與助攻得分破2000\n\t\t\t\n\t\t\t"
    ## [12] "\n\t\t\t\n\t\t\t\t[討論] D.Russell是不是骰子型球員?\n\t\t\t\n\t\t\t"            
    ## [13] "\n\t\t\t\n\t\t\t\tRe: [討論] NBA球員有拿過大滿貫的?\n\t\t\t\n\t\t\t"            
    ## [14] "\n\t\t\t\n\t\t\t\t[新聞] 尼克如何變強？ 何總：補進更好的防守者\n\t\t\t\n\t\t\t" 
    ## [15] "\n\t\t\t\n\t\t\t\tRe: [討論] NBA球員有拿過大滿貫的?\n\t\t\t\n\t\t\t"            
    ## [16] "\n\t\t\t\n\t\t\t\t[討論] 為什麼雙基奇搭配不起來？\n\t\t\t\n\t\t\t"              
    ## [17] "\n\t\t\t\n\t\t\t\t[討論] 浪花勇士是否是哈登永遠的痛?\n\t\t\t\n\t\t\t"           
    ## [18] "\n\t\t\t\n\t\t\t\t(本文已被刪除) [knic52976]\n\t\t\t\n\t\t\t"                   
    ## [19] "\n\t\t\t\n\t\t\t\t[討論] Rose是不是偷了Lebron的MVP啊\n\t\t\t\n\t\t\t"           
    ## [20] "\n\t\t\t\n\t\t\t\t[新聞] 勇士連3年60勝 公牛王朝後首見\n\t\t\t\n\t\t\t"

``` r
post_pushnum <- PTTContent %>% html_nodes(".nrec") %>% html_text() 
post_pushnum
```

    ##  [1] "79" "59" "X2" "29" "爆" "46" "26" "爆" "7"  "40" "21" "74" "17" "18"
    ## [15] ""   "19" "27" ""   "X6" "50"

``` r
post_author <- PTTContent %>% html_nodes(".author") %>% html_text() 
post_author
```

    ##  [1] "Rambo"       "Rambo"       "c1236"       "Price"       "arbcs"      
    ##  [6] "Yui5"        "JAL96"       "kadasaki"    "kadasaki"    "djviva"     
    ## [11] "adam7148"    "tiffanycute" "hayuyang"    "pttpepe"     "nogoodlaugh"
    ## [16] "eatk"        "yenyu73"     "-"           "knic52976"   "lovea"

``` r
PTT1<-"https://www.ptt.cc/bbs/NBA/index4627.html"
PTTContent1<-read_html(PTT1)
post_title1 <- PTTContent1 %>% html_nodes(".title") %>% html_text() 
post_title1
```

    ##  [1] "\n\t\t\t\n\t\t\t\t[Live] 勇士 @ 火箭\n\t\t\t\n\t\t\t"                           
    ##  [2] "\n\t\t\t\n\t\t\t\t[新聞] 年度教練競爭激烈 柯爾力挺丹東尼\n\t\t\t\n\t\t\t"       
    ##  [3] "\n\t\t\t\n\t\t\t\t[討論] 籃網RHJ這個球員......\n\t\t\t\n\t\t\t"                 
    ##  [4] "\n\t\t\t\n\t\t\t\t[BOX ] Bucks 118:108 Hornets 數據\n\t\t\t\n\t\t\t"            
    ##  [5] "\n\t\t\t\n\t\t\t\t[Live] 金塊 @ 拓荒者\n\t\t\t\n\t\t\t"                         
    ##  [6] "\n\t\t\t\n\t\t\t\t[BOX ] Timberwolves 115:114 Pacers 數據\n\t\t\t\n\t\t\t"      
    ##  [7] "\n\t\t\t\n\t\t\t\t[BOX ] Sixers 106:101 Nets 數據\n\t\t\t\n\t\t\t"              
    ##  [8] "\n\t\t\t\n\t\t\t\t[BOX ] Suns 91:95 Hawks 數據\n\t\t\t\n\t\t\t"                 
    ##  [9] "\n\t\t\t\n\t\t\t\t[新聞] 上場時間決定MVP？　哈登：我從未缺席比\n\t\t\t\n\t\t\t" 
    ## [10] "\n\t\t\t\n\t\t\t\t[BOX ] Heat 97:96 Pistons 數據\n\t\t\t\n\t\t\t"               
    ## [11] "\n\t\t\t\n\t\t\t\t[Live] 巫師 @ 湖人\n\t\t\t\n\t\t\t"                           
    ## [12] "\n\t\t\t\n\t\t\t\t[新聞] 林書豪關鍵走步失誤　籃網惜敗76人\n\t\t\t\n\t\t\t"      
    ## [13] "\n\t\t\t\n\t\t\t\t[BOX ] Warriors 113:106 Rockets 數據\n\t\t\t\n\t\t\t"         
    ## [14] "\n\t\t\t\n\t\t\t\t[新聞] 勇士「浪花兄弟」開轟　火箭哈登熄火吞敗\n\t\t\t\n\t\t\t"
    ## [15] "\n\t\t\t\n\t\t\t\t[討論] 沒KD 勇士還是不可小看\n\t\t\t\n\t\t\t"                 
    ## [16] "\n\t\t\t\n\t\t\t\tRe: [討論] 去年快艇如何守哈登買飯集錦\n\t\t\t\n\t\t\t"        
    ## [17] "\n\t\t\t\n\t\t\t\t[情報] Kerr fastest coach in American sports \n\t\t\t\n\t\t\t"
    ## [18] "\n\t\t\t\n\t\t\t\t[新聞] 林書豪在場能量加倍 籃網輸球也精彩\n\t\t\t\n\t\t\t"     
    ## [19] "\n\t\t\t\n\t\t\t\t[討論] 留KD或Curry？\n\t\t\t\n\t\t\t"                         
    ## [20] "\n\t\t\t\n\t\t\t\t[討論] 穩進季後賽的火箭，仍然最多一輪\n\t\t\t\n\t\t\t"

``` r
post_pushnum1 <- PTTContent1 %>% html_nodes(".nrec") %>% html_text() 
post_pushnum1
```

    ##  [1] "96" "30" "23" "37" "44" "51" "91" "20" "26" "21" "34" "29" "爆" "34"
    ## [15] "13" "17" "70" "2"  "爆" "X3"

``` r
post_author1 <- PTTContent1 %>% html_nodes(".author") %>% html_text() 
post_author1
```

    ##  [1] "Rambo"       "pneumo"      "ronharper"   "Rambo"       "Rambo"      
    ##  [6] "Rambo"       "Rambo"       "Rambo"       "zzyyxx77"    "Rambo"      
    ## [11] "Rambo"       "jhemezuo"    "Rambo"       "zzzz8931"    "feyako"     
    ## [16] "bluestaral"  "Angel0724"   "lcall"       "star1739456" "sunnycello"

``` r
PTT2<-"https://www.ptt.cc/bbs/NBA/index4626.html"
PTTContent2<-read_html(PTT2)
post_title2 <- PTTContent2 %>% html_nodes(".title") %>% html_text() 
post_title2
```

    ##  [1] "\n\t\t\t\n\t\t\t\t[討論]John Wall 算東區第一控了嗎？\n\t\t\t\n\t\t\t"             
    ##  [2] "\n\t\t\t\n\t\t\t\tRe: [情報] 甜瓜：禁藥名單太長，我會選擇中草藥\n\t\t\t\n\t\t\t"  
    ##  [3] "\n\t\t\t\n\t\t\t\t(本文已被刪除) [MrSatan]\n\t\t\t\n\t\t\t"                       
    ##  [4] "\n\t\t\t\n\t\t\t\t[新聞] 好腰高難度空接　Manu：看不懂他怎麼傳\n\t\t\t\n\t\t\t"    
    ##  [5] "\n\t\t\t\n\t\t\t\t[新聞] NBA／尼克將改變策略？ 何納塞克：下季將\n\t\t\t\n\t\t\t"  
    ##  [6] "\n\t\t\t\n\t\t\t\t[新聞] 馬刺大勝騎士 雷納德：沒有任何意義\n\t\t\t\n\t\t\t"       
    ##  [7] "\n\t\t\t\n\t\t\t\t[情報] 微笑刺客：若Rose最終去了馬刺不會讓我感\n\t\t\t\n\t\t\t"  
    ##  [8] "\n\t\t\t\n\t\t\t\tRe: [討論] 之前有球隊刻意輸比賽 控制對手嗎\n\t\t\t\n\t\t\t"     
    ##  [9] "\n\t\t\t\n\t\t\t\t[新聞] 女性總教練？ 主席席佛：希望快點出現\n\t\t\t\n\t\t\t"     
    ## [10] "\n\t\t\t\n\t\t\t\t[公告]多人水桶 \n\t\t\t\n\t\t\t"                                
    ## [11] "\n\t\t\t\n\t\t\t\tRe: [討論] NBA球員有拿過大滿貫的?\n\t\t\t\n\t\t\t"              
    ## [12] "\n\t\t\t\n\t\t\t\t[情報] 火箭差8顆三分打破單季三分進球數紀錄\n\t\t\t\n\t\t\t"     
    ## [13] "\n\t\t\t\n\t\t\t\t[討論] 球員綽號\n\t\t\t\n\t\t\t"                                
    ## [14] "\n\t\t\t\n\t\t\t\tRe: [新聞] 好腰高難度空接　Manu：看不懂他怎麼傳\n\t\t\t\n\t\t\t"
    ## [15] "\n\t\t\t\n\t\t\t\t[Live] 公鹿 @ 黃蜂\n\t\t\t\n\t\t\t"                             
    ## [16] "\n\t\t\t\n\t\t\t\t[Live] 灰狼 @ 溜馬\n\t\t\t\n\t\t\t"                             
    ## [17] "\n\t\t\t\n\t\t\t\t[Live] 七六人 @ 籃網\n\t\t\t\n\t\t\t"                           
    ## [18] "\n\t\t\t\n\t\t\t\t[Live] 太陽 @ 老鷹\n\t\t\t\n\t\t\t"                             
    ## [19] "\n\t\t\t\n\t\t\t\t[Live] 熱火 @ 活塞\n\t\t\t\n\t\t\t"                             
    ## [20] "\n\t\t\t\n\t\t\t\t(已被kadasaki刪除) <HANASUCIA> OP\n\t\t\t\n\t\t\t"

``` r
post_pushnum2 <- PTTContent2 %>% html_nodes(".nrec") %>% html_text() 
post_pushnum2
```

    ##  [1] "99" "2"  "1"  "69" "28" "59" "爆" "1"  "45" "爆" "1"  "38" "20" "15"
    ## [15] "4"  "16" "爆" "1"  "12" "X5"

``` r
post_author2 <- PTTContent2 %>% html_nodes(".author") %>% html_text() 
post_author2
```

    ##  [1] "h1212123tw"   "tadshift2"    "-"            "zzzz8931"    
    ##  [5] "iam168888888" "ccps970915"   "tmacor1"      "BBDurant"    
    ##  [9] "Gotham"       "namie810303"  "Jachu"        "Wall62"      
    ## [13] "ZaneTrout"    "steveparker"  "Rambo"        "Rambo"       
    ## [17] "Rambo"        "Rambo"        "Rambo"        "-"

``` r
PTT3<-"https://www.ptt.cc/bbs/NBA/index4625.html"
PTTContent3<-read_html(PTT3)
post_title3 <- PTTContent3 %>% html_nodes(".title") %>% html_text() 
post_title3
```

    ##  [1] "\n\t\t\t\n\t\t\t\tRe: [討論] 如果騎士在西區\n\t\t\t\n\t\t\t"                   
    ##  [2] "\n\t\t\t\n\t\t\t\t[情報] 甜瓜：禁藥名單太長，我會選擇中草藥\n\t\t\t\n\t\t\t"   
    ##  [3] "\n\t\t\t\n\t\t\t\tRe: [討論] Lebron被大衛李尻背部受傷???\n\t\t\t\n\t\t\t"      
    ##  [4] "\n\t\t\t\n\t\t\t\tRe: [情報] NBA Standings(2017.03.28)\n\t\t\t\n\t\t\t"        
    ##  [5] "\n\t\t\t\n\t\t\t\t[討論] NBA球員有拿過大滿貫的?\n\t\t\t\n\t\t\t"               
    ##  [6] "\n\t\t\t\n\t\t\t\t[討論] 東西勝場差～這些年的西強東弱\n\t\t\t\n\t\t\t"         
    ##  [7] "\n\t\t\t\n\t\t\t\t[新聞] 騎士近況低迷 詹姆斯：得找出解決方法\n\t\t\t\n\t\t\t"  
    ##  [8] "\n\t\t\t\n\t\t\t\t[專欄] 死豬不怕開水燙 尼克丟臉已成習慣\n\t\t\t\n\t\t\t"      
    ##  [9] "\n\t\t\t\n\t\t\t\tRe: [討論] NBA球員有拿過大滿貫的?\n\t\t\t\n\t\t\t"           
    ## [10] "\n\t\t\t\n\t\t\t\t[情報] Kobe：Booker有我想傳承給下一代球員的\n\t\t\t\n\t\t\t" 
    ## [11] "\n\t\t\t\n\t\t\t\t(已被namie810303刪除) <OGC789456123>引戰\n\t\t\t\n\t\t\t"    
    ## [12] "\n\t\t\t\n\t\t\t\tRe: [討論] 東西勝場差～這些年的西強東弱\n\t\t\t\n\t\t\t"     
    ## [13] "\n\t\t\t\n\t\t\t\t(已被kadasaki刪除) <knic52976> 1-2\n\t\t\t\n\t\t\t"          
    ## [14] "\n\t\t\t\n\t\t\t\t(本文已被刪除) [goodbad]\n\t\t\t\n\t\t\t"                    
    ## [15] "\n\t\t\t\n\t\t\t\t[新聞] 隊友藥檢未 甜瓜：我都呷中藥顧健康\n\t\t\t\n\t\t\t"    
    ## [16] "\n\t\t\t\n\t\t\t\tRe: [討論] NBA球員有拿過大滿貫的?\n\t\t\t\n\t\t\t"           
    ## [17] "\n\t\t\t\n\t\t\t\t[花邊] Steve Francis, Joe Smith 加入BIG3聯賽\n\t\t\t\n\t\t\t"
    ## [18] "\n\t\t\t\n\t\t\t\t(本文已被刪除) [hawoo]\n\t\t\t\n\t\t\t"                      
    ## [19] "\n\t\t\t\n\t\t\t\t[花邊] Kyrie Irving賽後獨自加練\n\t\t\t\n\t\t\t"             
    ## [20] "\n\t\t\t\n\t\t\t\t[情報] 控衛防守哪家強？ “Wall”成聯盟第一\n\t\t\t\n\t\t\t"

``` r
post_pushnum3 <- PTTContent3 %>% html_nodes(".nrec") %>% html_text() 
post_pushnum3
```

    ##  [1] "X1" "57" "18" "19" "28" "78" "61" "19" "19" "50" "X3" "25" "X1" "15"
    ## [15] "56" "29" "23" ""   "80" "76"

``` r
post_author3 <- PTTContent3 %>% html_nodes(".author") %>% html_text() 
post_author3
```

    ##  [1] "Turtle100"    "Yui5"         "iammatrix"    "cric335"     
    ##  [5] "chchang0820"  "liusim"       "adam7148"     "zzyyxx77"    
    ##  [9] "monmo"        "lovea"        "-"            "MK12"        
    ## [13] "-"            "-"            "royhsu425"    "Myosotis"    
    ## [17] "thnlkj0665"   "-"            "KyrieIrving1" "tmac0818"

``` r
PTT4<-"https://www.ptt.cc/bbs/NBA/index4624.html"
PTTContent4<-read_html(PTT4)
post_title4 <- PTTContent4 %>% html_nodes(".title") %>% html_text() 
post_title4
```

    ##  [1] "\n\t\t\t\n\t\t\t\t(已被namie810303刪除) <a102203028>引戰退\n\t\t\t\n\t\t\t"    
    ##  [2] "\n\t\t\t\n\t\t\t\tRe: [討論] 騎士東區第一的位置是不是不保了\n\t\t\t\n\t\t\t"   
    ##  [3] "\n\t\t\t\n\t\t\t\t[討論] 這場結束之後 是不是確定了西強東弱？\n\t\t\t\n\t\t\t"  
    ##  [4] "\n\t\t\t\n\t\t\t\t[討論] 騎士球隊CP值\n\t\t\t\n\t\t\t"                         
    ##  [5] "\n\t\t\t\n\t\t\t\t[新聞] 老大拒絕輪休 卻認為詹皇是例外\n\t\t\t\n\t\t\t"        
    ##  [6] "\n\t\t\t\n\t\t\t\t[新聞] 林書豪教得好 隊友會用中文說贏球\n\t\t\t\n\t\t\t"      
    ##  [7] "\n\t\t\t\n\t\t\t\t[討論] 騎士是不是為了避開熱火或公牛？\n\t\t\t\n\t\t\t"       
    ##  [8] "\n\t\t\t\n\t\t\t\t[新聞] 球迷為搏版面出狠招 不惜拿兒子祭旗\n\t\t\t\n\t\t\t"    
    ##  [9] "\n\t\t\t\n\t\t\t\t[新聞] 騎士慘敗給馬刺　跌下東區龍頭寶座\n\t\t\t\n\t\t\t"     
    ## [10] "\n\t\t\t\n\t\t\t\t(本文已被刪除) <AsakuraYume>\n\t\t\t\n\t\t\t"                
    ## [11] "\n\t\t\t\n\t\t\t\tRe: [新聞] 老大拒絕輪休 卻認為詹皇是例外\n\t\t\t\n\t\t\t"    
    ## [12] "\n\t\t\t\n\t\t\t\t[BOX ] Pelicans 100:108 Jazz 數據\n\t\t\t\n\t\t\t"           
    ## [13] "\n\t\t\t\n\t\t\t\t[新聞] 衛少第37次大三元 致勝一擊逆轉小牛\n\t\t\t\n\t\t\t"    
    ## [14] "\n\t\t\t\n\t\t\t\t[BOX ] Grizzlies 90:91 Kings 數據\n\t\t\t\n\t\t\t"           
    ## [15] "\n\t\t\t\n\t\t\t\t[新聞] 季中吞大補丸卻慘敗馬刺 詹皇寫一項最難\n\t\t\t\n\t\t\t"
    ## [16] "\n\t\t\t\n\t\t\t\t[討論] 之前有球隊刻意輸比賽 控制對手嗎\n\t\t\t\n\t\t\t"      
    ## [17] "\n\t\t\t\n\t\t\t\t[情報] 詹姆斯：我想讓我們能打得更好些\n\t\t\t\n\t\t\t"       
    ## [18] "\n\t\t\t\n\t\t\t\t[情報] Kawhi Leonard連續100場得分雙位數\n\t\t\t\n\t\t\t"     
    ## [19] "\n\t\t\t\n\t\t\t\t[討論] Lebron被大衛李尻背部受傷???\n\t\t\t\n\t\t\t"          
    ## [20] "\n\t\t\t\n\t\t\t\tRe: [情報] NBA Standings(2017.03.28)\n\t\t\t\n\t\t\t"

``` r
post_pushnum4 <- PTTContent4 %>% html_nodes(".nrec") %>% html_text() 
post_pushnum4
```

    ##  [1] ""   "4"  "爆" "21" "75" "37" "17" "14" "26" "18" "1"  "25" "30" "39"
    ## [15] "31" "22" "32" "37" "99" "爆"

``` r
post_author4 <- PTTContent4 %>% html_nodes(".author") %>% html_text() 
post_author4
```

    ##  [1] "-"           "j5826497110" "tiffanycute" "t13thbc"     "pttpepe"    
    ##  [6] "Assisi"      "Max11"       "abc7360393"  "JAL96"       "-"          
    ## [11] "ICHIKOnice"  "Rambo"       "MLbaseball"  "hungys"      "dameontree" 
    ## [16] "peace9527"   "knic52976"   "jimmy5680"   "chouvincent" "kadasaki"

``` r
PTT5<-"https://www.ptt.cc/bbs/NBA/index4623.html"
PTTContent5<-read_html(PTT5)
post_title5 <- PTTContent5 %>% html_nodes(".title") %>% html_text() 
post_title5
```

    ##  [1] "\n\t\t\t\n\t\t\t\t[討論] 騎馬大戰\n\t\t\t\n\t\t\t"                                
    ##  [2] "\n\t\t\t\n\t\t\t\t[Live] 雷霆 @ 小牛\n\t\t\t\n\t\t\t"                             
    ##  [3] "\n\t\t\t\n\t\t\t\t[情報] 東西區上週最佳球員：DeRozan, Harden\n\t\t\t\n\t\t\t"     
    ##  [4] "\n\t\t\t\n\t\t\t\t[情報] 國王有意撤換總管Vlade Divac\n\t\t\t\n\t\t\t"             
    ##  [5] "\n\t\t\t\n\t\t\t\t[花邊] Duncan：每次在家看到馬刺贏球我都會罵人\n\t\t\t\n\t\t\t"  
    ##  [6] "\n\t\t\t\n\t\t\t\t[情報] 湖人Buss家族內鬥結束,Jeanie掌權\n\t\t\t\n\t\t\t"         
    ##  [7] "\n\t\t\t\n\t\t\t\t[花邊] Kobe退休之後　最愛看這4名球星打球\n\t\t\t\n\t\t\t"       
    ##  [8] "\n\t\t\t\n\t\t\t\t[花邊] O'Neal：我曾給餐廳服務生付過四千美元小費\n\t\t\t\n\t\t\t"
    ##  [9] "\n\t\t\t\n\t\t\t\t[BOX ] Pistons 95:109 Knicks 數據\n\t\t\t\n\t\t\t"              
    ## [10] "\n\t\t\t\n\t\t\t\t[Live] 鵜鶘 @ 爵士\n\t\t\t\n\t\t\t"                             
    ## [11] "\n\t\t\t\n\t\t\t\t[BOX ] Magic 112:131 Raptors 數據\n\t\t\t\n\t\t\t"              
    ## [12] "\n\t\t\t\n\t\t\t\t[新聞] 不滿快艇遮湖人  歐尼爾嗆別擋住老子球衣\n\t\t\t\n\t\t\t"  
    ## [13] "\n\t\t\t\n\t\t\t\t(本文已被刪除) [a10141013]\n\t\t\t\n\t\t\t"                     
    ## [14] "\n\t\t\t\n\t\t\t\t[討論] 騎士東區第一的位置是不是不保了\n\t\t\t\n\t\t\t"          
    ## [15] "\n\t\t\t\n\t\t\t\t[BOX ] Cavaliers 74:103 Spurs 數據\n\t\t\t\n\t\t\t"             
    ## [16] "\n\t\t\t\n\t\t\t\t[討論] 騎士是 真藏招 還是 還在 磨合 ?\n\t\t\t\n\t\t\t"          
    ## [17] "\n\t\t\t\n\t\t\t\t[新聞] 馬刺痛宰騎士收5連勝 東部龍頭換人當\n\t\t\t\n\t\t\t"      
    ## [18] "\n\t\t\t\n\t\t\t\t[BOX ] Thunder 92:91 Mavericks 數據\n\t\t\t\n\t\t\t"            
    ## [19] "\n\t\t\t\n\t\t\t\tRe: [討論] 騎士東區第一的位置是不是不保了\n\t\t\t\n\t\t\t"      
    ## [20] "\n\t\t\t\n\t\t\t\t(已被namie810303刪除) <Lankavatara>1-6\n\t\t\t\n\t\t\t"

``` r
post_pushnum5 <- PTTContent5 %>% html_nodes(".nrec") %>% html_text() 
post_pushnum5
```

    ##  [1] "2"  "74" "19" "25" "爆" "9"  "64" "55" "30" "4"  "12" "34" "1"  "7" 
    ## [15] "爆" "75" "21" "68" "35" "37"

``` r
post_author5 <- PTTContent5 %>% html_nodes(".author") %>% html_text() 
post_author5
```

    ##  [1] "jojoii82"    "Rambo"       "Maxwell5566" "dragon803"   "Yui5"       
    ##  [6] "sezna"       "pneumo"      "bigDwinsch"  "Rambo"       "Rambo"      
    ## [11] "Rambo"       "meiyouo"     "-"           "CurryMvp"    "Rambo"      
    ## [16] "Turtle100"   "pneumo"      "Rambo"       "kingrichman" "-"

``` r
NBAdataframe <- data.frame(Title=c(post_title), PushNum=c(post_pushnum), Author=c(post_author))
NBAdataframe
```

    ##                                                                              Title
    ## 1            \n\t\t\t\n\t\t\t\t[BOX ] Nuggets 113:122 Blazers 數據\n\t\t\t\n\t\t\t
    ## 2             \n\t\t\t\n\t\t\t\t[BOX ] Wizards 119:108 Lakers 數據\n\t\t\t\n\t\t\t
    ## 3   \n\t\t\t\n\t\t\t\tRe: [新聞] 林書豪在場能量加倍 籃網輸球也精彩\n\t\t\t\n\t\t\t
    ## 4              \n\t\t\t\n\t\t\t\tRe: [討論] NBA球員有拿過大滿貫的?\n\t\t\t\n\t\t\t
    ## 5                       \n\t\t\t\n\t\t\t\tRe: [討論] 留KD或Curry？\n\t\t\t\n\t\t\t
    ## 6           \n\t\t\t\n\t\t\t\t[情報] ESPN:馬刺4：0擊敗去年東西冠軍\n\t\t\t\n\t\t\t
    ## 7   \n\t\t\t\n\t\t\t\t[新聞] 諾克奇33分轟前東家金塊　拓荒者老8之爭\n\t\t\t\n\t\t\t
    ## 8               \n\t\t\t\n\t\t\t\t[情報] NBA Standings(2017.03.29)\n\t\t\t\n\t\t\t
    ## 9                    \n\t\t\t\n\t\t\t\t[公告] NBA 板 開始舉辦樂透!\n\t\t\t\n\t\t\t
    ## 10        \n\t\t\t\n\t\t\t\t[外絮] Is it time to sit James Harden?\n\t\t\t\n\t\t\t
    ## 11 \n\t\t\t\n\t\t\t\t[新聞] 史上第一人！哈登總得分與助攻得分破2000\n\t\t\t\n\t\t\t
    ## 12             \n\t\t\t\n\t\t\t\t[討論] D.Russell是不是骰子型球員?\n\t\t\t\n\t\t\t
    ## 13             \n\t\t\t\n\t\t\t\tRe: [討論] NBA球員有拿過大滿貫的?\n\t\t\t\n\t\t\t
    ## 14  \n\t\t\t\n\t\t\t\t[新聞] 尼克如何變強？ 何總：補進更好的防守者\n\t\t\t\n\t\t\t
    ## 15             \n\t\t\t\n\t\t\t\tRe: [討論] NBA球員有拿過大滿貫的?\n\t\t\t\n\t\t\t
    ## 16               \n\t\t\t\n\t\t\t\t[討論] 為什麼雙基奇搭配不起來？\n\t\t\t\n\t\t\t
    ## 17            \n\t\t\t\n\t\t\t\t[討論] 浪花勇士是否是哈登永遠的痛?\n\t\t\t\n\t\t\t
    ## 18                    \n\t\t\t\n\t\t\t\t(本文已被刪除) [knic52976]\n\t\t\t\n\t\t\t
    ## 19            \n\t\t\t\n\t\t\t\t[討論] Rose是不是偷了Lebron的MVP啊\n\t\t\t\n\t\t\t
    ## 20           \n\t\t\t\n\t\t\t\t[新聞] 勇士連3年60勝 公牛王朝後首見\n\t\t\t\n\t\t\t
    ##    PushNum      Author
    ## 1       79       Rambo
    ## 2       59       Rambo
    ## 3       X2       c1236
    ## 4       29       Price
    ## 5       爆       arbcs
    ## 6       46        Yui5
    ## 7       26       JAL96
    ## 8       爆    kadasaki
    ## 9        7    kadasaki
    ## 10      40      djviva
    ## 11      21    adam7148
    ## 12      74 tiffanycute
    ## 13      17    hayuyang
    ## 14      18     pttpepe
    ## 15         nogoodlaugh
    ## 16      19        eatk
    ## 17      27     yenyu73
    ## 18                   -
    ## 19      X6   knic52976
    ## 20      50       lovea

``` r
NBAdataframe1 <- data.frame(Title=c(post_title1), PushNum=c(post_pushnum1), Author=c(post_author1))
NBAdataframe1
```

    ##                                                                              Title
    ## 1                             \n\t\t\t\n\t\t\t\t[Live] 勇士 @ 火箭\n\t\t\t\n\t\t\t
    ## 2         \n\t\t\t\n\t\t\t\t[新聞] 年度教練競爭激烈 柯爾力挺丹東尼\n\t\t\t\n\t\t\t
    ## 3                   \n\t\t\t\n\t\t\t\t[討論] 籃網RHJ這個球員......\n\t\t\t\n\t\t\t
    ## 4              \n\t\t\t\n\t\t\t\t[BOX ] Bucks 118:108 Hornets 數據\n\t\t\t\n\t\t\t
    ## 5                           \n\t\t\t\n\t\t\t\t[Live] 金塊 @ 拓荒者\n\t\t\t\n\t\t\t
    ## 6        \n\t\t\t\n\t\t\t\t[BOX ] Timberwolves 115:114 Pacers 數據\n\t\t\t\n\t\t\t
    ## 7                \n\t\t\t\n\t\t\t\t[BOX ] Sixers 106:101 Nets 數據\n\t\t\t\n\t\t\t
    ## 8                   \n\t\t\t\n\t\t\t\t[BOX ] Suns 91:95 Hawks 數據\n\t\t\t\n\t\t\t
    ## 9   \n\t\t\t\n\t\t\t\t[新聞] 上場時間決定MVP？　哈登：我從未缺席比\n\t\t\t\n\t\t\t
    ## 10                \n\t\t\t\n\t\t\t\t[BOX ] Heat 97:96 Pistons 數據\n\t\t\t\n\t\t\t
    ## 11                            \n\t\t\t\n\t\t\t\t[Live] 巫師 @ 湖人\n\t\t\t\n\t\t\t
    ## 12       \n\t\t\t\n\t\t\t\t[新聞] 林書豪關鍵走步失誤　籃網惜敗76人\n\t\t\t\n\t\t\t
    ## 13          \n\t\t\t\n\t\t\t\t[BOX ] Warriors 113:106 Rockets 數據\n\t\t\t\n\t\t\t
    ## 14 \n\t\t\t\n\t\t\t\t[新聞] 勇士「浪花兄弟」開轟　火箭哈登熄火吞敗\n\t\t\t\n\t\t\t
    ## 15                  \n\t\t\t\n\t\t\t\t[討論] 沒KD 勇士還是不可小看\n\t\t\t\n\t\t\t
    ## 16         \n\t\t\t\n\t\t\t\tRe: [討論] 去年快艇如何守哈登買飯集錦\n\t\t\t\n\t\t\t
    ## 17 \n\t\t\t\n\t\t\t\t[情報] Kerr fastest coach in American sports \n\t\t\t\n\t\t\t
    ## 18      \n\t\t\t\n\t\t\t\t[新聞] 林書豪在場能量加倍 籃網輸球也精彩\n\t\t\t\n\t\t\t
    ## 19                          \n\t\t\t\n\t\t\t\t[討論] 留KD或Curry？\n\t\t\t\n\t\t\t
    ## 20         \n\t\t\t\n\t\t\t\t[討論] 穩進季後賽的火箭，仍然最多一輪\n\t\t\t\n\t\t\t
    ##    PushNum      Author
    ## 1       96       Rambo
    ## 2       30      pneumo
    ## 3       23   ronharper
    ## 4       37       Rambo
    ## 5       44       Rambo
    ## 6       51       Rambo
    ## 7       91       Rambo
    ## 8       20       Rambo
    ## 9       26    zzyyxx77
    ## 10      21       Rambo
    ## 11      34       Rambo
    ## 12      29    jhemezuo
    ## 13      爆       Rambo
    ## 14      34    zzzz8931
    ## 15      13      feyako
    ## 16      17  bluestaral
    ## 17      70   Angel0724
    ## 18       2       lcall
    ## 19      爆 star1739456
    ## 20      X3  sunnycello

``` r
NBAdataframe2 <- data.frame(Title=c(post_title2), PushNum=c(post_pushnum2), Author=c(post_author2))
NBAdataframe2
```

    ##                                                                                Title
    ## 1               \n\t\t\t\n\t\t\t\t[討論]John Wall 算東區第一控了嗎？\n\t\t\t\n\t\t\t
    ## 2    \n\t\t\t\n\t\t\t\tRe: [情報] 甜瓜：禁藥名單太長，我會選擇中草藥\n\t\t\t\n\t\t\t
    ## 3                         \n\t\t\t\n\t\t\t\t(本文已被刪除) [MrSatan]\n\t\t\t\n\t\t\t
    ## 4      \n\t\t\t\n\t\t\t\t[新聞] 好腰高難度空接　Manu：看不懂他怎麼傳\n\t\t\t\n\t\t\t
    ## 5    \n\t\t\t\n\t\t\t\t[新聞] NBA／尼克將改變策略？ 何納塞克：下季將\n\t\t\t\n\t\t\t
    ## 6         \n\t\t\t\n\t\t\t\t[新聞] 馬刺大勝騎士 雷納德：沒有任何意義\n\t\t\t\n\t\t\t
    ## 7    \n\t\t\t\n\t\t\t\t[情報] 微笑刺客：若Rose最終去了馬刺不會讓我感\n\t\t\t\n\t\t\t
    ## 8       \n\t\t\t\n\t\t\t\tRe: [討論] 之前有球隊刻意輸比賽 控制對手嗎\n\t\t\t\n\t\t\t
    ## 9       \n\t\t\t\n\t\t\t\t[新聞] 女性總教練？ 主席席佛：希望快點出現\n\t\t\t\n\t\t\t
    ## 10                                 \n\t\t\t\n\t\t\t\t[公告]多人水桶 \n\t\t\t\n\t\t\t
    ## 11               \n\t\t\t\n\t\t\t\tRe: [討論] NBA球員有拿過大滿貫的?\n\t\t\t\n\t\t\t
    ## 12      \n\t\t\t\n\t\t\t\t[情報] 火箭差8顆三分打破單季三分進球數紀錄\n\t\t\t\n\t\t\t
    ## 13                                 \n\t\t\t\n\t\t\t\t[討論] 球員綽號\n\t\t\t\n\t\t\t
    ## 14 \n\t\t\t\n\t\t\t\tRe: [新聞] 好腰高難度空接　Manu：看不懂他怎麼傳\n\t\t\t\n\t\t\t
    ## 15                              \n\t\t\t\n\t\t\t\t[Live] 公鹿 @ 黃蜂\n\t\t\t\n\t\t\t
    ## 16                              \n\t\t\t\n\t\t\t\t[Live] 灰狼 @ 溜馬\n\t\t\t\n\t\t\t
    ## 17                            \n\t\t\t\n\t\t\t\t[Live] 七六人 @ 籃網\n\t\t\t\n\t\t\t
    ## 18                              \n\t\t\t\n\t\t\t\t[Live] 太陽 @ 老鷹\n\t\t\t\n\t\t\t
    ## 19                              \n\t\t\t\n\t\t\t\t[Live] 熱火 @ 活塞\n\t\t\t\n\t\t\t
    ## 20               \n\t\t\t\n\t\t\t\t(已被kadasaki刪除) <HANASUCIA> OP\n\t\t\t\n\t\t\t
    ##    PushNum       Author
    ## 1       99   h1212123tw
    ## 2        2    tadshift2
    ## 3        1            -
    ## 4       69     zzzz8931
    ## 5       28 iam168888888
    ## 6       59   ccps970915
    ## 7       爆      tmacor1
    ## 8        1     BBDurant
    ## 9       45       Gotham
    ## 10      爆  namie810303
    ## 11       1        Jachu
    ## 12      38       Wall62
    ## 13      20    ZaneTrout
    ## 14      15  steveparker
    ## 15       4        Rambo
    ## 16      16        Rambo
    ## 17      爆        Rambo
    ## 18       1        Rambo
    ## 19      12        Rambo
    ## 20      X5            -

``` r
NBAdataframe3 <- data.frame(Title=c(post_title3), PushNum=c(post_pushnum3), Author=c(post_author3))
NBAdataframe3
```

    ##                                                                             Title
    ## 1                     \n\t\t\t\n\t\t\t\tRe: [討論] 如果騎士在西區\n\t\t\t\n\t\t\t
    ## 2     \n\t\t\t\n\t\t\t\t[情報] 甜瓜：禁藥名單太長，我會選擇中草藥\n\t\t\t\n\t\t\t
    ## 3        \n\t\t\t\n\t\t\t\tRe: [討論] Lebron被大衛李尻背部受傷???\n\t\t\t\n\t\t\t
    ## 4          \n\t\t\t\n\t\t\t\tRe: [情報] NBA Standings(2017.03.28)\n\t\t\t\n\t\t\t
    ## 5                 \n\t\t\t\n\t\t\t\t[討論] NBA球員有拿過大滿貫的?\n\t\t\t\n\t\t\t
    ## 6           \n\t\t\t\n\t\t\t\t[討論] 東西勝場差～這些年的西強東弱\n\t\t\t\n\t\t\t
    ## 7    \n\t\t\t\n\t\t\t\t[新聞] 騎士近況低迷 詹姆斯：得找出解決方法\n\t\t\t\n\t\t\t
    ## 8        \n\t\t\t\n\t\t\t\t[專欄] 死豬不怕開水燙 尼克丟臉已成習慣\n\t\t\t\n\t\t\t
    ## 9             \n\t\t\t\n\t\t\t\tRe: [討論] NBA球員有拿過大滿貫的?\n\t\t\t\n\t\t\t
    ## 10  \n\t\t\t\n\t\t\t\t[情報] Kobe：Booker有我想傳承給下一代球員的\n\t\t\t\n\t\t\t
    ## 11     \n\t\t\t\n\t\t\t\t(已被namie810303刪除) <OGC789456123>引戰\n\t\t\t\n\t\t\t
    ## 12      \n\t\t\t\n\t\t\t\tRe: [討論] 東西勝場差～這些年的西強東弱\n\t\t\t\n\t\t\t
    ## 13           \n\t\t\t\n\t\t\t\t(已被kadasaki刪除) <knic52976> 1-2\n\t\t\t\n\t\t\t
    ## 14                     \n\t\t\t\n\t\t\t\t(本文已被刪除) [goodbad]\n\t\t\t\n\t\t\t
    ## 15     \n\t\t\t\n\t\t\t\t[新聞] 隊友藥檢未 甜瓜：我都呷中藥顧健康\n\t\t\t\n\t\t\t
    ## 16            \n\t\t\t\n\t\t\t\tRe: [討論] NBA球員有拿過大滿貫的?\n\t\t\t\n\t\t\t
    ## 17 \n\t\t\t\n\t\t\t\t[花邊] Steve Francis, Joe Smith 加入BIG3聯賽\n\t\t\t\n\t\t\t
    ## 18                       \n\t\t\t\n\t\t\t\t(本文已被刪除) [hawoo]\n\t\t\t\n\t\t\t
    ## 19              \n\t\t\t\n\t\t\t\t[花邊] Kyrie Irving賽後獨自加練\n\t\t\t\n\t\t\t
    ## 20     \n\t\t\t\n\t\t\t\t[情報] 控衛防守哪家強？ “Wall”成聯盟第一\n\t\t\t\n\t\t\t
    ##    PushNum       Author
    ## 1       X1    Turtle100
    ## 2       57         Yui5
    ## 3       18    iammatrix
    ## 4       19      cric335
    ## 5       28  chchang0820
    ## 6       78       liusim
    ## 7       61     adam7148
    ## 8       19     zzyyxx77
    ## 9       19        monmo
    ## 10      50        lovea
    ## 11      X3            -
    ## 12      25         MK12
    ## 13      X1            -
    ## 14      15            -
    ## 15      56    royhsu425
    ## 16      29     Myosotis
    ## 17      23   thnlkj0665
    ## 18                    -
    ## 19      80 KyrieIrving1
    ## 20      76     tmac0818

``` r
NBAdataframe4 <- data.frame(Title=c(post_title4), PushNum=c(post_pushnum4), Author=c(post_author4))
NBAdataframe4
```

    ##                                                                             Title
    ## 1      \n\t\t\t\n\t\t\t\t(已被namie810303刪除) <a102203028>引戰退\n\t\t\t\n\t\t\t
    ## 2     \n\t\t\t\n\t\t\t\tRe: [討論] 騎士東區第一的位置是不是不保了\n\t\t\t\n\t\t\t
    ## 3    \n\t\t\t\n\t\t\t\t[討論] 這場結束之後 是不是確定了西強東弱？\n\t\t\t\n\t\t\t
    ## 4                           \n\t\t\t\n\t\t\t\t[討論] 騎士球隊CP值\n\t\t\t\n\t\t\t
    ## 5          \n\t\t\t\n\t\t\t\t[新聞] 老大拒絕輪休 卻認為詹皇是例外\n\t\t\t\n\t\t\t
    ## 6        \n\t\t\t\n\t\t\t\t[新聞] 林書豪教得好 隊友會用中文說贏球\n\t\t\t\n\t\t\t
    ## 7         \n\t\t\t\n\t\t\t\t[討論] 騎士是不是為了避開熱火或公牛？\n\t\t\t\n\t\t\t
    ## 8      \n\t\t\t\n\t\t\t\t[新聞] 球迷為搏版面出狠招 不惜拿兒子祭旗\n\t\t\t\n\t\t\t
    ## 9       \n\t\t\t\n\t\t\t\t[新聞] 騎士慘敗給馬刺　跌下東區龍頭寶座\n\t\t\t\n\t\t\t
    ## 10                 \n\t\t\t\n\t\t\t\t(本文已被刪除) <AsakuraYume>\n\t\t\t\n\t\t\t
    ## 11     \n\t\t\t\n\t\t\t\tRe: [新聞] 老大拒絕輪休 卻認為詹皇是例外\n\t\t\t\n\t\t\t
    ## 12            \n\t\t\t\n\t\t\t\t[BOX ] Pelicans 100:108 Jazz 數據\n\t\t\t\n\t\t\t
    ## 13     \n\t\t\t\n\t\t\t\t[新聞] 衛少第37次大三元 致勝一擊逆轉小牛\n\t\t\t\n\t\t\t
    ## 14            \n\t\t\t\n\t\t\t\t[BOX ] Grizzlies 90:91 Kings 數據\n\t\t\t\n\t\t\t
    ## 15 \n\t\t\t\n\t\t\t\t[新聞] 季中吞大補丸卻慘敗馬刺 詹皇寫一項最難\n\t\t\t\n\t\t\t
    ## 16       \n\t\t\t\n\t\t\t\t[討論] 之前有球隊刻意輸比賽 控制對手嗎\n\t\t\t\n\t\t\t
    ## 17        \n\t\t\t\n\t\t\t\t[情報] 詹姆斯：我想讓我們能打得更好些\n\t\t\t\n\t\t\t
    ## 18      \n\t\t\t\n\t\t\t\t[情報] Kawhi Leonard連續100場得分雙位數\n\t\t\t\n\t\t\t
    ## 19           \n\t\t\t\n\t\t\t\t[討論] Lebron被大衛李尻背部受傷???\n\t\t\t\n\t\t\t
    ## 20         \n\t\t\t\n\t\t\t\tRe: [情報] NBA Standings(2017.03.28)\n\t\t\t\n\t\t\t
    ##    PushNum      Author
    ## 1                    -
    ## 2        4 j5826497110
    ## 3       爆 tiffanycute
    ## 4       21     t13thbc
    ## 5       75     pttpepe
    ## 6       37      Assisi
    ## 7       17       Max11
    ## 8       14  abc7360393
    ## 9       26       JAL96
    ## 10      18           -
    ## 11       1  ICHIKOnice
    ## 12      25       Rambo
    ## 13      30  MLbaseball
    ## 14      39      hungys
    ## 15      31  dameontree
    ## 16      22   peace9527
    ## 17      32   knic52976
    ## 18      37   jimmy5680
    ## 19      99 chouvincent
    ## 20      爆    kadasaki

``` r
NBAdataframe5 <- data.frame(Title=c(post_title5), PushNum=c(post_pushnum5), Author=c(post_author5))
NBAdataframe5
```

    ##                                                                                Title
    ## 1                                  \n\t\t\t\n\t\t\t\t[討論] 騎馬大戰\n\t\t\t\n\t\t\t
    ## 2                               \n\t\t\t\n\t\t\t\t[Live] 雷霆 @ 小牛\n\t\t\t\n\t\t\t
    ## 3       \n\t\t\t\n\t\t\t\t[情報] 東西區上週最佳球員：DeRozan, Harden\n\t\t\t\n\t\t\t
    ## 4               \n\t\t\t\n\t\t\t\t[情報] 國王有意撤換總管Vlade Divac\n\t\t\t\n\t\t\t
    ## 5    \n\t\t\t\n\t\t\t\t[花邊] Duncan：每次在家看到馬刺贏球我都會罵人\n\t\t\t\n\t\t\t
    ## 6           \n\t\t\t\n\t\t\t\t[情報] 湖人Buss家族內鬥結束,Jeanie掌權\n\t\t\t\n\t\t\t
    ## 7         \n\t\t\t\n\t\t\t\t[花邊] Kobe退休之後　最愛看這4名球星打球\n\t\t\t\n\t\t\t
    ## 8  \n\t\t\t\n\t\t\t\t[花邊] O'Neal：我曾給餐廳服務生付過四千美元小費\n\t\t\t\n\t\t\t
    ## 9                \n\t\t\t\n\t\t\t\t[BOX ] Pistons 95:109 Knicks 數據\n\t\t\t\n\t\t\t
    ## 10                              \n\t\t\t\n\t\t\t\t[Live] 鵜鶘 @ 爵士\n\t\t\t\n\t\t\t
    ## 11               \n\t\t\t\n\t\t\t\t[BOX ] Magic 112:131 Raptors 數據\n\t\t\t\n\t\t\t
    ## 12   \n\t\t\t\n\t\t\t\t[新聞] 不滿快艇遮湖人  歐尼爾嗆別擋住老子球衣\n\t\t\t\n\t\t\t
    ## 13                      \n\t\t\t\n\t\t\t\t(本文已被刪除) [a10141013]\n\t\t\t\n\t\t\t
    ## 14           \n\t\t\t\n\t\t\t\t[討論] 騎士東區第一的位置是不是不保了\n\t\t\t\n\t\t\t
    ## 15              \n\t\t\t\n\t\t\t\t[BOX ] Cavaliers 74:103 Spurs 數據\n\t\t\t\n\t\t\t
    ## 16           \n\t\t\t\n\t\t\t\t[討論] 騎士是 真藏招 還是 還在 磨合 ?\n\t\t\t\n\t\t\t
    ## 17       \n\t\t\t\n\t\t\t\t[新聞] 馬刺痛宰騎士收5連勝 東部龍頭換人當\n\t\t\t\n\t\t\t
    ## 18             \n\t\t\t\n\t\t\t\t[BOX ] Thunder 92:91 Mavericks 數據\n\t\t\t\n\t\t\t
    ## 19       \n\t\t\t\n\t\t\t\tRe: [討論] 騎士東區第一的位置是不是不保了\n\t\t\t\n\t\t\t
    ## 20          \n\t\t\t\n\t\t\t\t(已被namie810303刪除) <Lankavatara>1-6\n\t\t\t\n\t\t\t
    ##    PushNum      Author
    ## 1        2    jojoii82
    ## 2       74       Rambo
    ## 3       19 Maxwell5566
    ## 4       25   dragon803
    ## 5       爆        Yui5
    ## 6        9       sezna
    ## 7       64      pneumo
    ## 8       55  bigDwinsch
    ## 9       30       Rambo
    ## 10       4       Rambo
    ## 11      12       Rambo
    ## 12      34     meiyouo
    ## 13       1           -
    ## 14       7    CurryMvp
    ## 15      爆       Rambo
    ## 16      75   Turtle100
    ## 17      21      pneumo
    ## 18      68       Rambo
    ## 19      35 kingrichman
    ## 20      37           -

``` r
dataframeAll<-rbind(NBAdataframe,NBAdataframe1,NBAdataframe2,NBAdataframe3,NBAdataframe4,NBAdataframe5)
dataframeAll
```

    ##                                                                                 Title
    ## 1               \n\t\t\t\n\t\t\t\t[BOX ] Nuggets 113:122 Blazers 數據\n\t\t\t\n\t\t\t
    ## 2                \n\t\t\t\n\t\t\t\t[BOX ] Wizards 119:108 Lakers 數據\n\t\t\t\n\t\t\t
    ## 3      \n\t\t\t\n\t\t\t\tRe: [新聞] 林書豪在場能量加倍 籃網輸球也精彩\n\t\t\t\n\t\t\t
    ## 4                 \n\t\t\t\n\t\t\t\tRe: [討論] NBA球員有拿過大滿貫的?\n\t\t\t\n\t\t\t
    ## 5                          \n\t\t\t\n\t\t\t\tRe: [討論] 留KD或Curry？\n\t\t\t\n\t\t\t
    ## 6              \n\t\t\t\n\t\t\t\t[情報] ESPN:馬刺4：0擊敗去年東西冠軍\n\t\t\t\n\t\t\t
    ## 7      \n\t\t\t\n\t\t\t\t[新聞] 諾克奇33分轟前東家金塊　拓荒者老8之爭\n\t\t\t\n\t\t\t
    ## 8                  \n\t\t\t\n\t\t\t\t[情報] NBA Standings(2017.03.29)\n\t\t\t\n\t\t\t
    ## 9                       \n\t\t\t\n\t\t\t\t[公告] NBA 板 開始舉辦樂透!\n\t\t\t\n\t\t\t
    ## 10           \n\t\t\t\n\t\t\t\t[外絮] Is it time to sit James Harden?\n\t\t\t\n\t\t\t
    ## 11    \n\t\t\t\n\t\t\t\t[新聞] 史上第一人！哈登總得分與助攻得分破2000\n\t\t\t\n\t\t\t
    ## 12                \n\t\t\t\n\t\t\t\t[討論] D.Russell是不是骰子型球員?\n\t\t\t\n\t\t\t
    ## 13                \n\t\t\t\n\t\t\t\tRe: [討論] NBA球員有拿過大滿貫的?\n\t\t\t\n\t\t\t
    ## 14     \n\t\t\t\n\t\t\t\t[新聞] 尼克如何變強？ 何總：補進更好的防守者\n\t\t\t\n\t\t\t
    ## 15                \n\t\t\t\n\t\t\t\tRe: [討論] NBA球員有拿過大滿貫的?\n\t\t\t\n\t\t\t
    ## 16                  \n\t\t\t\n\t\t\t\t[討論] 為什麼雙基奇搭配不起來？\n\t\t\t\n\t\t\t
    ## 17               \n\t\t\t\n\t\t\t\t[討論] 浪花勇士是否是哈登永遠的痛?\n\t\t\t\n\t\t\t
    ## 18                       \n\t\t\t\n\t\t\t\t(本文已被刪除) [knic52976]\n\t\t\t\n\t\t\t
    ## 19               \n\t\t\t\n\t\t\t\t[討論] Rose是不是偷了Lebron的MVP啊\n\t\t\t\n\t\t\t
    ## 20              \n\t\t\t\n\t\t\t\t[新聞] 勇士連3年60勝 公牛王朝後首見\n\t\t\t\n\t\t\t
    ## 21                               \n\t\t\t\n\t\t\t\t[Live] 勇士 @ 火箭\n\t\t\t\n\t\t\t
    ## 22           \n\t\t\t\n\t\t\t\t[新聞] 年度教練競爭激烈 柯爾力挺丹東尼\n\t\t\t\n\t\t\t
    ## 23                     \n\t\t\t\n\t\t\t\t[討論] 籃網RHJ這個球員......\n\t\t\t\n\t\t\t
    ## 24                \n\t\t\t\n\t\t\t\t[BOX ] Bucks 118:108 Hornets 數據\n\t\t\t\n\t\t\t
    ## 25                             \n\t\t\t\n\t\t\t\t[Live] 金塊 @ 拓荒者\n\t\t\t\n\t\t\t
    ## 26          \n\t\t\t\n\t\t\t\t[BOX ] Timberwolves 115:114 Pacers 數據\n\t\t\t\n\t\t\t
    ## 27                  \n\t\t\t\n\t\t\t\t[BOX ] Sixers 106:101 Nets 數據\n\t\t\t\n\t\t\t
    ## 28                     \n\t\t\t\n\t\t\t\t[BOX ] Suns 91:95 Hawks 數據\n\t\t\t\n\t\t\t
    ## 29     \n\t\t\t\n\t\t\t\t[新聞] 上場時間決定MVP？　哈登：我從未缺席比\n\t\t\t\n\t\t\t
    ## 30                   \n\t\t\t\n\t\t\t\t[BOX ] Heat 97:96 Pistons 數據\n\t\t\t\n\t\t\t
    ## 31                               \n\t\t\t\n\t\t\t\t[Live] 巫師 @ 湖人\n\t\t\t\n\t\t\t
    ## 32          \n\t\t\t\n\t\t\t\t[新聞] 林書豪關鍵走步失誤　籃網惜敗76人\n\t\t\t\n\t\t\t
    ## 33             \n\t\t\t\n\t\t\t\t[BOX ] Warriors 113:106 Rockets 數據\n\t\t\t\n\t\t\t
    ## 34    \n\t\t\t\n\t\t\t\t[新聞] 勇士「浪花兄弟」開轟　火箭哈登熄火吞敗\n\t\t\t\n\t\t\t
    ## 35                     \n\t\t\t\n\t\t\t\t[討論] 沒KD 勇士還是不可小看\n\t\t\t\n\t\t\t
    ## 36            \n\t\t\t\n\t\t\t\tRe: [討論] 去年快艇如何守哈登買飯集錦\n\t\t\t\n\t\t\t
    ## 37    \n\t\t\t\n\t\t\t\t[情報] Kerr fastest coach in American sports \n\t\t\t\n\t\t\t
    ## 38         \n\t\t\t\n\t\t\t\t[新聞] 林書豪在場能量加倍 籃網輸球也精彩\n\t\t\t\n\t\t\t
    ## 39                             \n\t\t\t\n\t\t\t\t[討論] 留KD或Curry？\n\t\t\t\n\t\t\t
    ## 40            \n\t\t\t\n\t\t\t\t[討論] 穩進季後賽的火箭，仍然最多一輪\n\t\t\t\n\t\t\t
    ## 41               \n\t\t\t\n\t\t\t\t[討論]John Wall 算東區第一控了嗎？\n\t\t\t\n\t\t\t
    ## 42    \n\t\t\t\n\t\t\t\tRe: [情報] 甜瓜：禁藥名單太長，我會選擇中草藥\n\t\t\t\n\t\t\t
    ## 43                         \n\t\t\t\n\t\t\t\t(本文已被刪除) [MrSatan]\n\t\t\t\n\t\t\t
    ## 44      \n\t\t\t\n\t\t\t\t[新聞] 好腰高難度空接　Manu：看不懂他怎麼傳\n\t\t\t\n\t\t\t
    ## 45    \n\t\t\t\n\t\t\t\t[新聞] NBA／尼克將改變策略？ 何納塞克：下季將\n\t\t\t\n\t\t\t
    ## 46         \n\t\t\t\n\t\t\t\t[新聞] 馬刺大勝騎士 雷納德：沒有任何意義\n\t\t\t\n\t\t\t
    ## 47    \n\t\t\t\n\t\t\t\t[情報] 微笑刺客：若Rose最終去了馬刺不會讓我感\n\t\t\t\n\t\t\t
    ## 48       \n\t\t\t\n\t\t\t\tRe: [討論] 之前有球隊刻意輸比賽 控制對手嗎\n\t\t\t\n\t\t\t
    ## 49       \n\t\t\t\n\t\t\t\t[新聞] 女性總教練？ 主席席佛：希望快點出現\n\t\t\t\n\t\t\t
    ## 50                                  \n\t\t\t\n\t\t\t\t[公告]多人水桶 \n\t\t\t\n\t\t\t
    ## 51                \n\t\t\t\n\t\t\t\tRe: [討論] NBA球員有拿過大滿貫的?\n\t\t\t\n\t\t\t
    ## 52       \n\t\t\t\n\t\t\t\t[情報] 火箭差8顆三分打破單季三分進球數紀錄\n\t\t\t\n\t\t\t
    ## 53                                  \n\t\t\t\n\t\t\t\t[討論] 球員綽號\n\t\t\t\n\t\t\t
    ## 54  \n\t\t\t\n\t\t\t\tRe: [新聞] 好腰高難度空接　Manu：看不懂他怎麼傳\n\t\t\t\n\t\t\t
    ## 55                               \n\t\t\t\n\t\t\t\t[Live] 公鹿 @ 黃蜂\n\t\t\t\n\t\t\t
    ## 56                               \n\t\t\t\n\t\t\t\t[Live] 灰狼 @ 溜馬\n\t\t\t\n\t\t\t
    ## 57                             \n\t\t\t\n\t\t\t\t[Live] 七六人 @ 籃網\n\t\t\t\n\t\t\t
    ## 58                               \n\t\t\t\n\t\t\t\t[Live] 太陽 @ 老鷹\n\t\t\t\n\t\t\t
    ## 59                               \n\t\t\t\n\t\t\t\t[Live] 熱火 @ 活塞\n\t\t\t\n\t\t\t
    ## 60                \n\t\t\t\n\t\t\t\t(已被kadasaki刪除) <HANASUCIA> OP\n\t\t\t\n\t\t\t
    ## 61                        \n\t\t\t\n\t\t\t\tRe: [討論] 如果騎士在西區\n\t\t\t\n\t\t\t
    ## 62        \n\t\t\t\n\t\t\t\t[情報] 甜瓜：禁藥名單太長，我會選擇中草藥\n\t\t\t\n\t\t\t
    ## 63           \n\t\t\t\n\t\t\t\tRe: [討論] Lebron被大衛李尻背部受傷???\n\t\t\t\n\t\t\t
    ## 64             \n\t\t\t\n\t\t\t\tRe: [情報] NBA Standings(2017.03.28)\n\t\t\t\n\t\t\t
    ## 65                    \n\t\t\t\n\t\t\t\t[討論] NBA球員有拿過大滿貫的?\n\t\t\t\n\t\t\t
    ## 66              \n\t\t\t\n\t\t\t\t[討論] 東西勝場差～這些年的西強東弱\n\t\t\t\n\t\t\t
    ## 67       \n\t\t\t\n\t\t\t\t[新聞] 騎士近況低迷 詹姆斯：得找出解決方法\n\t\t\t\n\t\t\t
    ## 68           \n\t\t\t\n\t\t\t\t[專欄] 死豬不怕開水燙 尼克丟臉已成習慣\n\t\t\t\n\t\t\t
    ## 69                \n\t\t\t\n\t\t\t\tRe: [討論] NBA球員有拿過大滿貫的?\n\t\t\t\n\t\t\t
    ## 70      \n\t\t\t\n\t\t\t\t[情報] Kobe：Booker有我想傳承給下一代球員的\n\t\t\t\n\t\t\t
    ## 71         \n\t\t\t\n\t\t\t\t(已被namie810303刪除) <OGC789456123>引戰\n\t\t\t\n\t\t\t
    ## 72          \n\t\t\t\n\t\t\t\tRe: [討論] 東西勝場差～這些年的西強東弱\n\t\t\t\n\t\t\t
    ## 73               \n\t\t\t\n\t\t\t\t(已被kadasaki刪除) <knic52976> 1-2\n\t\t\t\n\t\t\t
    ## 74                         \n\t\t\t\n\t\t\t\t(本文已被刪除) [goodbad]\n\t\t\t\n\t\t\t
    ## 75         \n\t\t\t\n\t\t\t\t[新聞] 隊友藥檢未 甜瓜：我都呷中藥顧健康\n\t\t\t\n\t\t\t
    ## 76                \n\t\t\t\n\t\t\t\tRe: [討論] NBA球員有拿過大滿貫的?\n\t\t\t\n\t\t\t
    ## 77     \n\t\t\t\n\t\t\t\t[花邊] Steve Francis, Joe Smith 加入BIG3聯賽\n\t\t\t\n\t\t\t
    ## 78                           \n\t\t\t\n\t\t\t\t(本文已被刪除) [hawoo]\n\t\t\t\n\t\t\t
    ## 79                  \n\t\t\t\n\t\t\t\t[花邊] Kyrie Irving賽後獨自加練\n\t\t\t\n\t\t\t
    ## 80         \n\t\t\t\n\t\t\t\t[情報] 控衛防守哪家強？ “Wall”成聯盟第一\n\t\t\t\n\t\t\t
    ## 81         \n\t\t\t\n\t\t\t\t(已被namie810303刪除) <a102203028>引戰退\n\t\t\t\n\t\t\t
    ## 82        \n\t\t\t\n\t\t\t\tRe: [討論] 騎士東區第一的位置是不是不保了\n\t\t\t\n\t\t\t
    ## 83       \n\t\t\t\n\t\t\t\t[討論] 這場結束之後 是不是確定了西強東弱？\n\t\t\t\n\t\t\t
    ## 84                              \n\t\t\t\n\t\t\t\t[討論] 騎士球隊CP值\n\t\t\t\n\t\t\t
    ## 85             \n\t\t\t\n\t\t\t\t[新聞] 老大拒絕輪休 卻認為詹皇是例外\n\t\t\t\n\t\t\t
    ## 86           \n\t\t\t\n\t\t\t\t[新聞] 林書豪教得好 隊友會用中文說贏球\n\t\t\t\n\t\t\t
    ## 87            \n\t\t\t\n\t\t\t\t[討論] 騎士是不是為了避開熱火或公牛？\n\t\t\t\n\t\t\t
    ## 88         \n\t\t\t\n\t\t\t\t[新聞] 球迷為搏版面出狠招 不惜拿兒子祭旗\n\t\t\t\n\t\t\t
    ## 89          \n\t\t\t\n\t\t\t\t[新聞] 騎士慘敗給馬刺　跌下東區龍頭寶座\n\t\t\t\n\t\t\t
    ## 90                     \n\t\t\t\n\t\t\t\t(本文已被刪除) <AsakuraYume>\n\t\t\t\n\t\t\t
    ## 91         \n\t\t\t\n\t\t\t\tRe: [新聞] 老大拒絕輪休 卻認為詹皇是例外\n\t\t\t\n\t\t\t
    ## 92                \n\t\t\t\n\t\t\t\t[BOX ] Pelicans 100:108 Jazz 數據\n\t\t\t\n\t\t\t
    ## 93         \n\t\t\t\n\t\t\t\t[新聞] 衛少第37次大三元 致勝一擊逆轉小牛\n\t\t\t\n\t\t\t
    ## 94                \n\t\t\t\n\t\t\t\t[BOX ] Grizzlies 90:91 Kings 數據\n\t\t\t\n\t\t\t
    ## 95     \n\t\t\t\n\t\t\t\t[新聞] 季中吞大補丸卻慘敗馬刺 詹皇寫一項最難\n\t\t\t\n\t\t\t
    ## 96           \n\t\t\t\n\t\t\t\t[討論] 之前有球隊刻意輸比賽 控制對手嗎\n\t\t\t\n\t\t\t
    ## 97            \n\t\t\t\n\t\t\t\t[情報] 詹姆斯：我想讓我們能打得更好些\n\t\t\t\n\t\t\t
    ## 98          \n\t\t\t\n\t\t\t\t[情報] Kawhi Leonard連續100場得分雙位數\n\t\t\t\n\t\t\t
    ## 99               \n\t\t\t\n\t\t\t\t[討論] Lebron被大衛李尻背部受傷???\n\t\t\t\n\t\t\t
    ## 100            \n\t\t\t\n\t\t\t\tRe: [情報] NBA Standings(2017.03.28)\n\t\t\t\n\t\t\t
    ## 101                                 \n\t\t\t\n\t\t\t\t[討論] 騎馬大戰\n\t\t\t\n\t\t\t
    ## 102                              \n\t\t\t\n\t\t\t\t[Live] 雷霆 @ 小牛\n\t\t\t\n\t\t\t
    ## 103      \n\t\t\t\n\t\t\t\t[情報] 東西區上週最佳球員：DeRozan, Harden\n\t\t\t\n\t\t\t
    ## 104              \n\t\t\t\n\t\t\t\t[情報] 國王有意撤換總管Vlade Divac\n\t\t\t\n\t\t\t
    ## 105   \n\t\t\t\n\t\t\t\t[花邊] Duncan：每次在家看到馬刺贏球我都會罵人\n\t\t\t\n\t\t\t
    ## 106          \n\t\t\t\n\t\t\t\t[情報] 湖人Buss家族內鬥結束,Jeanie掌權\n\t\t\t\n\t\t\t
    ## 107        \n\t\t\t\n\t\t\t\t[花邊] Kobe退休之後　最愛看這4名球星打球\n\t\t\t\n\t\t\t
    ## 108 \n\t\t\t\n\t\t\t\t[花邊] O'Neal：我曾給餐廳服務生付過四千美元小費\n\t\t\t\n\t\t\t
    ## 109               \n\t\t\t\n\t\t\t\t[BOX ] Pistons 95:109 Knicks 數據\n\t\t\t\n\t\t\t
    ## 110                              \n\t\t\t\n\t\t\t\t[Live] 鵜鶘 @ 爵士\n\t\t\t\n\t\t\t
    ## 111               \n\t\t\t\n\t\t\t\t[BOX ] Magic 112:131 Raptors 數據\n\t\t\t\n\t\t\t
    ## 112   \n\t\t\t\n\t\t\t\t[新聞] 不滿快艇遮湖人  歐尼爾嗆別擋住老子球衣\n\t\t\t\n\t\t\t
    ## 113                      \n\t\t\t\n\t\t\t\t(本文已被刪除) [a10141013]\n\t\t\t\n\t\t\t
    ## 114           \n\t\t\t\n\t\t\t\t[討論] 騎士東區第一的位置是不是不保了\n\t\t\t\n\t\t\t
    ## 115              \n\t\t\t\n\t\t\t\t[BOX ] Cavaliers 74:103 Spurs 數據\n\t\t\t\n\t\t\t
    ## 116           \n\t\t\t\n\t\t\t\t[討論] 騎士是 真藏招 還是 還在 磨合 ?\n\t\t\t\n\t\t\t
    ## 117       \n\t\t\t\n\t\t\t\t[新聞] 馬刺痛宰騎士收5連勝 東部龍頭換人當\n\t\t\t\n\t\t\t
    ## 118             \n\t\t\t\n\t\t\t\t[BOX ] Thunder 92:91 Mavericks 數據\n\t\t\t\n\t\t\t
    ## 119       \n\t\t\t\n\t\t\t\tRe: [討論] 騎士東區第一的位置是不是不保了\n\t\t\t\n\t\t\t
    ## 120          \n\t\t\t\n\t\t\t\t(已被namie810303刪除) <Lankavatara>1-6\n\t\t\t\n\t\t\t
    ##     PushNum       Author
    ## 1        79        Rambo
    ## 2        59        Rambo
    ## 3        X2        c1236
    ## 4        29        Price
    ## 5        爆        arbcs
    ## 6        46         Yui5
    ## 7        26        JAL96
    ## 8        爆     kadasaki
    ## 9         7     kadasaki
    ## 10       40       djviva
    ## 11       21     adam7148
    ## 12       74  tiffanycute
    ## 13       17     hayuyang
    ## 14       18      pttpepe
    ## 15           nogoodlaugh
    ## 16       19         eatk
    ## 17       27      yenyu73
    ## 18                     -
    ## 19       X6    knic52976
    ## 20       50        lovea
    ## 21       96        Rambo
    ## 22       30       pneumo
    ## 23       23    ronharper
    ## 24       37        Rambo
    ## 25       44        Rambo
    ## 26       51        Rambo
    ## 27       91        Rambo
    ## 28       20        Rambo
    ## 29       26     zzyyxx77
    ## 30       21        Rambo
    ## 31       34        Rambo
    ## 32       29     jhemezuo
    ## 33       爆        Rambo
    ## 34       34     zzzz8931
    ## 35       13       feyako
    ## 36       17   bluestaral
    ## 37       70    Angel0724
    ## 38        2        lcall
    ## 39       爆  star1739456
    ## 40       X3   sunnycello
    ## 41       99   h1212123tw
    ## 42        2    tadshift2
    ## 43        1            -
    ## 44       69     zzzz8931
    ## 45       28 iam168888888
    ## 46       59   ccps970915
    ## 47       爆      tmacor1
    ## 48        1     BBDurant
    ## 49       45       Gotham
    ## 50       爆  namie810303
    ## 51        1        Jachu
    ## 52       38       Wall62
    ## 53       20    ZaneTrout
    ## 54       15  steveparker
    ## 55        4        Rambo
    ## 56       16        Rambo
    ## 57       爆        Rambo
    ## 58        1        Rambo
    ## 59       12        Rambo
    ## 60       X5            -
    ## 61       X1    Turtle100
    ## 62       57         Yui5
    ## 63       18    iammatrix
    ## 64       19      cric335
    ## 65       28  chchang0820
    ## 66       78       liusim
    ## 67       61     adam7148
    ## 68       19     zzyyxx77
    ## 69       19        monmo
    ## 70       50        lovea
    ## 71       X3            -
    ## 72       25         MK12
    ## 73       X1            -
    ## 74       15            -
    ## 75       56    royhsu425
    ## 76       29     Myosotis
    ## 77       23   thnlkj0665
    ## 78                     -
    ## 79       80 KyrieIrving1
    ## 80       76     tmac0818
    ## 81                     -
    ## 82        4  j5826497110
    ## 83       爆  tiffanycute
    ## 84       21      t13thbc
    ## 85       75      pttpepe
    ## 86       37       Assisi
    ## 87       17        Max11
    ## 88       14   abc7360393
    ## 89       26        JAL96
    ## 90       18            -
    ## 91        1   ICHIKOnice
    ## 92       25        Rambo
    ## 93       30   MLbaseball
    ## 94       39       hungys
    ## 95       31   dameontree
    ## 96       22    peace9527
    ## 97       32    knic52976
    ## 98       37    jimmy5680
    ## 99       99  chouvincent
    ## 100      爆     kadasaki
    ## 101       2     jojoii82
    ## 102      74        Rambo
    ## 103      19  Maxwell5566
    ## 104      25    dragon803
    ## 105      爆         Yui5
    ## 106       9        sezna
    ## 107      64       pneumo
    ## 108      55   bigDwinsch
    ## 109      30        Rambo
    ## 110       4        Rambo
    ## 111      12        Rambo
    ## 112      34      meiyouo
    ## 113       1            -
    ## 114       7     CurryMvp
    ## 115      爆        Rambo
    ## 116      75    Turtle100
    ## 117      21       pneumo
    ## 118      68        Rambo
    ## 119      35  kingrichman
    ## 120      37            -

``` r
##read_html
##html_nodes
##html_text
```

爬蟲結果呈現
------------

``` r
knitr::kable(
    dataframeAll[1:100,c("Title","PushNum","Author")])
```

| Title                                             | PushNum | Author       |
|:--------------------------------------------------|:--------|:-------------|
| \[BOX \] Nuggets 113:122 Blazers 數據             | 79      | Rambo        |
| \[BOX \] Wizards 119:108 Lakers 數據              | 59      | Rambo        |
| Re: \[新聞\] 林書豪在場能量加倍 籃網輸球也精彩    | X2      | c1236        |
| Re: \[討論\] NBA球員有拿過大滿貫的?               | 29      | Price        |
| Re: \[討論\] 留KD或Curry？                        | 爆      | arbcs        |
| \[情報\] ESPN:馬刺4：0擊敗去年東西冠軍            | 46      | Yui5         |
| \[新聞\] 諾克奇33分轟前東家金塊　拓荒者老8之爭    | 26      | JAL96        |
| \[情報\] NBA Standings(2017.03.29)                | 爆      | kadasaki     |
| \[公告\] NBA 板 開始舉辦樂透!                     | 7       | kadasaki     |
| \[外絮\] Is it time to sit James Harden?          | 40      | djviva       |
| \[新聞\] 史上第一人！哈登總得分與助攻得分破2000   | 21      | adam7148     |
| \[討論\] D.Russell是不是骰子型球員?               | 74      | tiffanycute  |
| Re: \[討論\] NBA球員有拿過大滿貫的?               | 17      | hayuyang     |
| \[新聞\] 尼克如何變強？ 何總：補進更好的防守者    | 18      | pttpepe      |
| Re: \[討論\] NBA球員有拿過大滿貫的?               |         | nogoodlaugh  |
| \[討論\] 為什麼雙基奇搭配不起來？                 | 19      | eatk         |
| \[討論\] 浪花勇士是否是哈登永遠的痛?              | 27      | yenyu73      |
| (本文已被刪除) \[knic52976\]                      |         | -            |
| \[討論\] Rose是不是偷了Lebron的MVP啊              | X6      | knic52976    |
| \[新聞\] 勇士連3年60勝 公牛王朝後首見             | 50      | lovea        |
| \[Live\] 勇士 @ 火箭                              | 96      | Rambo        |
| \[新聞\] 年度教練競爭激烈 柯爾力挺丹東尼          | 30      | pneumo       |
| \[討論\] 籃網RHJ這個球員......                    | 23      | ronharper    |
| \[BOX \] Bucks 118:108 Hornets 數據               | 37      | Rambo        |
| \[Live\] 金塊 @ 拓荒者                            | 44      | Rambo        |
| \[BOX \] Timberwolves 115:114 Pacers 數據         | 51      | Rambo        |
| \[BOX \] Sixers 106:101 Nets 數據                 | 91      | Rambo        |
| \[BOX \] Suns 91:95 Hawks 數據                    | 20      | Rambo        |
| \[新聞\] 上場時間決定MVP？　哈登：我從未缺席比    | 26      | zzyyxx77     |
| \[BOX \] Heat 97:96 Pistons 數據                  | 21      | Rambo        |
| \[Live\] 巫師 @ 湖人                              | 34      | Rambo        |
| \[新聞\] 林書豪關鍵走步失誤　籃網惜敗76人         | 29      | jhemezuo     |
| \[BOX \] Warriors 113:106 Rockets 數據            | 爆      | Rambo        |
| \[新聞\] 勇士「浪花兄弟」開轟　火箭哈登熄火吞敗   | 34      | zzzz8931     |
| \[討論\] 沒KD 勇士還是不可小看                    | 13      | feyako       |
| Re: \[討論\] 去年快艇如何守哈登買飯集錦           | 17      | bluestaral   |
| \[情報\] Kerr fastest coach in American sports    | 70      | Angel0724    |
| \[新聞\] 林書豪在場能量加倍 籃網輸球也精彩        | 2       | lcall        |
| \[討論\] 留KD或Curry？                            | 爆      | star1739456  |
| \[討論\] 穩進季後賽的火箭，仍然最多一輪           | X3      | sunnycello   |
| \[討論\]John Wall 算東區第一控了嗎？              | 99      | h1212123tw   |
| Re: \[情報\] 甜瓜：禁藥名單太長，我會選擇中草藥   | 2       | tadshift2    |
| (本文已被刪除) \[MrSatan\]                        | 1       | -            |
| \[新聞\] 好腰高難度空接　Manu：看不懂他怎麼傳     | 69      | zzzz8931     |
| \[新聞\] NBA／尼克將改變策略？ 何納塞克：下季將   | 28      | iam168888888 |
| \[新聞\] 馬刺大勝騎士 雷納德：沒有任何意義        | 59      | ccps970915   |
| \[情報\] 微笑刺客：若Rose最終去了馬刺不會讓我感   | 爆      | tmacor1      |
| Re: \[討論\] 之前有球隊刻意輸比賽 控制對手嗎      | 1       | BBDurant     |
| \[新聞\] 女性總教練？ 主席席佛：希望快點出現      | 45      | Gotham       |
| \[公告\]多人水桶                                  | 爆      | namie810303  |
| Re: \[討論\] NBA球員有拿過大滿貫的?               | 1       | Jachu        |
| \[情報\] 火箭差8顆三分打破單季三分進球數紀錄      | 38      | Wall62       |
| \[討論\] 球員綽號                                 | 20      | ZaneTrout    |
| Re: \[新聞\] 好腰高難度空接　Manu：看不懂他怎麼傳 | 15      | steveparker  |
| \[Live\] 公鹿 @ 黃蜂                              | 4       | Rambo        |
| \[Live\] 灰狼 @ 溜馬                              | 16      | Rambo        |
| \[Live\] 七六人 @ 籃網                            | 爆      | Rambo        |
| \[Live\] 太陽 @ 老鷹                              | 1       | Rambo        |
| \[Live\] 熱火 @ 活塞                              | 12      | Rambo        |
| (已被kadasaki刪除) <HANASUCIA> OP                 | X5      | -            |
| Re: \[討論\] 如果騎士在西區                       | X1      | Turtle100    |
| \[情報\] 甜瓜：禁藥名單太長，我會選擇中草藥       | 57      | Yui5         |
| Re: \[討論\] Lebron被大衛李尻背部受傷???          | 18      | iammatrix    |
| Re: \[情報\] NBA Standings(2017.03.28)            | 19      | cric335      |
| \[討論\] NBA球員有拿過大滿貫的?                   | 28      | chchang0820  |
| \[討論\] 東西勝場差～這些年的西強東弱             | 78      | liusim       |
| \[新聞\] 騎士近況低迷 詹姆斯：得找出解決方法      | 61      | adam7148     |
| \[專欄\] 死豬不怕開水燙 尼克丟臉已成習慣          | 19      | zzyyxx77     |
| Re: \[討論\] NBA球員有拿過大滿貫的?               | 19      | monmo        |
| \[情報\] Kobe：Booker有我想傳承給下一代球員的     | 50      | lovea        |
| (已被namie810303刪除) <OGC789456123>引戰          | X3      | -            |
| Re: \[討論\] 東西勝場差～這些年的西強東弱         | 25      | MK12         |
| (已被kadasaki刪除) <knic52976> 1-2                | X1      | -            |
| (本文已被刪除) \[goodbad\]                        | 15      | -            |
| \[新聞\] 隊友藥檢未 甜瓜：我都呷中藥顧健康        | 56      | royhsu425    |
| Re: \[討論\] NBA球員有拿過大滿貫的?               | 29      | Myosotis     |
| \[花邊\] Steve Francis, Joe Smith 加入BIG3聯賽    | 23      | thnlkj0665   |
| (本文已被刪除) \[hawoo\]                          |         | -            |
| \[花邊\] Kyrie Irving賽後獨自加練                 | 80      | KyrieIrving1 |
| \[情報\] 控衛防守哪家強？ “Wall”成聯盟第一        | 76      | tmac0818     |
| (已被namie810303刪除) <a102203028>引戰退          |         | -            |
| Re: \[討論\] 騎士東區第一的位置是不是不保了       | 4       | j5826497110  |
| \[討論\] 這場結束之後 是不是確定了西強東弱？      | 爆      | tiffanycute  |
| \[討論\] 騎士球隊CP值                             | 21      | t13thbc      |
| \[新聞\] 老大拒絕輪休 卻認為詹皇是例外            | 75      | pttpepe      |
| \[新聞\] 林書豪教得好 隊友會用中文說贏球          | 37      | Assisi       |
| \[討論\] 騎士是不是為了避開熱火或公牛？           | 17      | Max11        |
| \[新聞\] 球迷為搏版面出狠招 不惜拿兒子祭旗        | 14      | abc7360393   |
| \[新聞\] 騎士慘敗給馬刺　跌下東區龍頭寶座         | 26      | JAL96        |
| (本文已被刪除) <AsakuraYume>                      | 18      | -            |
| Re: \[新聞\] 老大拒絕輪休 卻認為詹皇是例外        | 1       | ICHIKOnice   |
| \[BOX \] Pelicans 100:108 Jazz 數據               | 25      | Rambo        |
| \[新聞\] 衛少第37次大三元 致勝一擊逆轉小牛        | 30      | MLbaseball   |
| \[BOX \] Grizzlies 90:91 Kings 數據               | 39      | hungys       |
| \[新聞\] 季中吞大補丸卻慘敗馬刺 詹皇寫一項最難    | 31      | dameontree   |
| \[討論\] 之前有球隊刻意輸比賽 控制對手嗎          | 22      | peace9527    |
| \[情報\] 詹姆斯：我想讓我們能打得更好些           | 32      | knic52976    |
| \[情報\] Kawhi Leonard連續100場得分雙位數         | 37      | jimmy5680    |
| \[討論\] Lebron被大衛李尻背部受傷???              | 99      | chouvincent  |
| Re: \[情報\] NBA Standings(2017.03.28)            | 爆      | kadasaki     |

解釋爬蟲結果
------------

``` r
dim(dataframeAll)
```

    ## [1] 120   3

共爬120個標題，有Title , PushNum , Author 這三個欄位

``` r
table(dataframeAll$Author)
```

    ## 
    ##            -     adam7148        arbcs        c1236       djviva 
    ##           11            2            1            1            1 
    ##         eatk     hayuyang        JAL96     kadasaki    knic52976 
    ##            1            1            2            3            2 
    ##        lovea  nogoodlaugh        Price      pttpepe        Rambo 
    ##            2            1            1            2           23 
    ##  tiffanycute      yenyu73         Yui5    Angel0724   bluestaral 
    ##            2            1            3            1            1 
    ##       feyako     jhemezuo        lcall       pneumo    ronharper 
    ##            1            1            1            3            1 
    ##  star1739456   sunnycello     zzyyxx77     zzzz8931     BBDurant 
    ##            1            1            2            2            1 
    ##   ccps970915       Gotham   h1212123tw iam168888888        Jachu 
    ##            1            1            1            1            1 
    ##  namie810303  steveparker    tadshift2      tmacor1       Wall62 
    ##            1            1            1            1            1 
    ##    ZaneTrout  chchang0820      cric335    iammatrix KyrieIrving1 
    ##            1            1            1            1            1 
    ##       liusim         MK12        monmo     Myosotis    royhsu425 
    ##            1            1            1            1            1 
    ##   thnlkj0665     tmac0818    Turtle100   abc7360393       Assisi 
    ##            1            1            2            1            1 
    ##  chouvincent   dameontree       hungys   ICHIKOnice  j5826497110 
    ##            1            1            1            1            1 
    ##    jimmy5680        Max11   MLbaseball    peace9527      t13thbc 
    ##            1            1            1            1            1 
    ##   bigDwinsch     CurryMvp    dragon803     jojoii82  kingrichman 
    ##            1            1            1            1            1 
    ##  Maxwell5566      meiyouo        sezna 
    ##            1            1            1

作者Rambo 文章數是23篇

因為我不會運用for迴圈，後來研究了很久發現可以連續複製好幾次就可以爬到很多筆了!
