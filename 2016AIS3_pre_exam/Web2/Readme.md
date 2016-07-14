# 2016 AIS3 pre-exam : Web2
Category: Web, Points: 2  

## Description
Give you a url, please find the flag.

## Write-up
轉址轉闢轉逆！   
這題其實非常簡單，一進去會看到顯示panel.php部分的程式碼，只要非127.0.0.1連過去就會被<del>嘲諷</del>阻擋，但是原本應該包在else裡面的flag顯示部分並沒有包起來，造成flag還是有在短暫的幾毫秒時間內顯示出來。  
使用curl去連panel.php秒解。

## Keypoint
- 了解PHP原理