# 2016 AIS3 pre-exam : Crypto1
Category: Crypto, Points: 1  

## Description
Give you a encrypt code, please decrypt it.

## Hint
XOR

## Write-up
這題主辦沒提示還真的沒想到XOR...    
方法一：把檔案丟到 [XOR Cracker](https://wiremask.eu/tools/xor-cracker/)去解，每個key length都嘗試一遍  
方法二：待補  
解完會得到一個flag，但是丟上去會說Key Error，認真看了flag，會發現中間有個可疑個"!"，"i!ea"...你是說"idea"嗎？改完送出就過了...！Magic x2  

## Keypoint
- XOR