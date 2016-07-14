# 2016 AIS3 pre-exam : Crypto2
Category: Crypto, Points: 2  

## Description
Give you a url, please find the code.

## Write-up
真。Web4，懷疑題目有漏洞...(ry  
進到網站，會發現網址多了expire跟auth，前者是根據現在的unix timestamp生成，後面則是用flag+expire=`$expire`去做sha1 hash生成的，網頁上會顯示這一頁原始碼（部分），仔細看會發現第一個if中間的判斷式``if(sha1($secret . "$qstr") === $auth)``和最下面的else生成的expire及auth是一樣的，因此，條件式是成立的。唯一沒有成立的是最裡面的``if($expire < time(0))``，此時會發現$expire和$qstr雖然都是取expire=xxx，但是取的方法不一樣，$expire是透過$_GET來去抓取網址中最後一個expire變數，而$qstr則是抓取"?"後面第一個expire=xxx，因此在網址最後面加上``&expire=9999999999999999``就可以順利解開拿到flag！  

## Keypoint
- 了解PHP原理