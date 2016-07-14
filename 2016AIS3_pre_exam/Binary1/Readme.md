# 2016 AIS3 pre-exam : Binary1
Category: Binary, Points: 1  

## Description
Give you a file, please find the flag.

## Write-up
1. 拿到一個檔案，用file指令去確認，發現是一個64 bit的ELF。
2. 用IDA Pro去開啟這個檔案，發現裡面有main及verify函式。簡單來說，就是執行時輸入一串字，程式會逐字去做運算，看運算結果是否和encrypted一樣。
3. 將verify及encrypted抓出來，撰寫程式逐字爆破運算。

## Keypoint
- 逆向工程