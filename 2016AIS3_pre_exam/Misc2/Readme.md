# 2016 AIS3 pre-exam : Misc2
Category: Misc, Points: 2  

## Description
Give you a file and please find the flag.  

## Hint
7zip  

## Write-up
這一題其實難度不高，唯一比較麻煩的是要撰寫程式。  
解這題，首先你會需要先使用hex viewer(Ex: xxd)檢視檔案，會發現這個檔案的開頭是'7Z'，因此可以先猜測這個檔案是一個7zip的壓縮檔案，可是當你用7zip來解壓縮的時候會發先解壓縮失敗，7zip不認為這是一個7z壓縮檔。  
此時，上Wikipedia搜尋7z條目，會發現右邊有一個欄位寫Magic Number : '7', 'z', 0xBC, 0xAF, 0x27, 0x1C，Magic Number在Programming上可以當作檔案識別的方法，因此會發現這個檔案的開頭7Z似乎錯了，把它改成7z之後7zip就可以辨識到壓縮檔了，但嘗試解壓縮會發現有密碼，於是便嘗試著使用檢視壓縮檔，因為壓縮檔加密有分兩類，解壓縮時要密碼及檢視要密碼，第一層屬於前者，所以可以正確地看到裡面，裡面有兩個亂碼檔案，一個是亂碼開頭一樣是7Z的壓縮檔案，另一個則是0B的空白檔，於是就試著用裡面兩個檔案的檔名來嘗試解壓縮這個。幸運的，0B的檔名正好是密碼，於是就解開了！  
第二層壓縮檔和第一層是一樣的，用同樣的方法解開即可。但是解到第三層發現，裡面的檔案不太一樣，一樣有一個亂碼檔案，但少了0B空白檔案，多了一個secret.txt，又亂碼檔案的檔名沒辦法解開這一層壓縮檔案，此時，不知道哪來的靈機一動，把上一層的密碼拿來解這一層，於是猜怎麼著？過了！Magic！
後續解壓縮都是一樣的動作，先改Magic Number，再用secret.txt中的密碼去解下一層的壓縮檔，但當進行到十來次的時候，發現裡面Always有一個壓縮檔案跟secret.txt，而且每次解壓縮檔案緊縮小幾個KB，按照這個規律，不知道要解幾時幾百次，因此只好撰寫程式來破這題。  

```
# This is psedocode, not python code!
while True:
	if not file_exist("/path/to/old/secret.txt"):
		break
	orig = open("/path/to/old/7z/file", "rb")
	content = read(orig)
	close(orig)
	newfile = open("/path/to/new/7z/file", "wb")
	newfile.write(str.encode('7z') + content[2:])
	close(newfile)
	secret = open("/path/to/old/secret.txt", "r")
	pwd = read(secret)
	close(secret)
	subprocess("/path/to/7z", " e ", "/path/to/new/7z/file", " -p", pwd, " -Ctemp", "-y")
	move_file("/path/to/new/secret.txt", "/path/to/old/secret.txt")
	move_file("/path/to/new/7z/file", "/path/to/old/7z/file")
	
```
當程式因為找不到secret.txt而噴錯的時候，flag.txt就出來了！Magic！

## Keypoint
- 7zip
- magic number
- write code