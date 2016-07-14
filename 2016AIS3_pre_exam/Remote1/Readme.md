# 2016 AIS3 pre-exam : Remote1
Category: Remote, Points: 1  

## Description
Give you a url and a file, please find the flag.

## Hint
- seed is important!
- ntp.ntu.edu.tw

## Write-up
1. 拿到一個檔案，用file指令去確認，發現是一個64 bit的ELF。
2. 用IDA Pro去開啟這個檔案，看完反解的Code，大意是說輸入一個數字，只要和他遠端連線時產生的亂數吻合就會噴flag。
3. srand用的是現在時間當成seed，因此首先要確保本地時間跟遠端是一致的，可以透過ntp協定去完成。
4. 撰寫程式，連線上去之後產生一個亂數過去就過了。（網路悲劇就會發生延遲而產生亂數不同）  

## Keypoint
- 逆向工程
- C語言的rand, srand