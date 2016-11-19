# 2015 CSIE CTF

* [RSA (crypto)](#rsa-crypto)
* [mayday (crypto)](#mayday-crypto)
* [Alien (crypto)](#Alien-crypto)
* [WebBabyFirst (Web)](#WebBabyFirst)
* [Mission (Web)](#Mission)
* [Login as admin 1 (Web)](#Login)
* [Eve (forensic)](#Eve)
* [What is that (misc)](#What_is_that)
* [Large (misc)](#Large)
* [LLARGE (misc)](#LLARGE)
* [zxcvb (misc)](#zxcvb)

<h2 id = "rsa-crypto">RSA (crypto)</h2>

提示 `just RSA`

已知資訊：密文 c，加密金鑰 public key (e, n)，又

```python
m = int(open('flag').read().strip().encode('hex'), 16)
```

所以是 flag，經由一串轉換變成明文 m

但 p, q 是 random

```python
p = randprime(2 ** 157, 2 ** 158)
q = randprime(2 ** 157, 2 ** 158)
```

已知 n，又

```
n = p * q
```

[質因數分解](http://factordb.com/)

這個網頁是抓 database，不是所有數都有解，剛好這題的 n 之前有人解開過

```
p = 244568058927274035851630625490731151685151358429
q = 282282802054792109028071238910250727429434271943
```

先備知識：[尤拉定理 Euler's Theorem](http://140.127.223.1/senior/speech/93/fu931127.pdf)

這網頁還不錯，中文的，有用簡單的數字舉例，後面還有加入加解密跟 RSA 的介紹

```
c = m^e mod n
m = c^d mod n
m = (m^e)^d mod n
ed = 1 mod ∅(n)
∅(n) = ∅(p) ∗ ∅(q) = (p - 1) ∗ (q - 1)
d = inverse(e) mod lcm((p - 1), (q - 1))
```

獲得解密金鑰 private key (d, n) 後，算出明文 m

m 的由來是打開 flag 檔案 -> 讀取 -> 轉成十六進位 -> 轉成十進位

中間的 `strip( )` 是移除字串中首尾指定的字元

但括號中並沒有指定任何字元，直接忽略

把 m 轉回十六進位，再轉回字串，得到 flag

<h2 id = "mayday-crypto">mayday (crypto)</h2>

已知：`e = 7`，分別在七個不同的 module n 下加密，得到七個不同的密文

有一種 RSA Attack 叫 [Hastad’s Broadcast Attack](https://crypto.stanford.edu/~dabo/papers/RSA-survey.pdf)

同一串明文，經由 k 個不同的 public key (e, n) 加密

當 e 值夠小，且所有的 e 都相等（只有 n 不同）、所有的 n 要兩兩互質

只要 k >= e，就可以用 CRT(Chinese Remainder Theorem) 求得明文 m

(有空再補 code)

<h2 id = "Alien-crypto">Alien (crypto)</h2>

```
flag is CTF{The decrypted message removing all spaces and punctuation marks}
```

用 google 搜尋 Alien Language

[題目跟這個長得很像](http://www.shipbrook.net/jeff/tencton/)

依照題目一個個尋找後，發現有兩個字母是從上圖找到，剩下的都出現在下圖

還發現有句點 -> .

猜測上圖是大寫，下圖是小寫

```
New planet found. Inhabitants are hydrocarbon lifeforms with a similar mathematics and logic.
```

把空格跟標點符號刪掉就是 flag 了

<h2 id = "WebBabyFirst">WebBabyFirst (Web)</h2>

**Flag 1**

檢查元素

```vbscript-html
<h3>Flag 1</h3>
        Here is the flag 1: <code><!-- Q1RGezBoX3kwdV9jNG5fNTMzXzdoM19oN21sX2MwbW0zbjd9 --></code><br>
```

base64 decode

`CTF{0h_y0u_c4n_533_7h3_h7ml_c0mm3n7}`

**Flag 2**

提示：Snoopy 只想吃 cookie

firefox 的 Cookies Manager 或是用 burp 看 cookie

丟到 url decode

```
Q1RGe2QzbDFjMTB1NV9jMDBrMTM1ISE1bjAwcHlfbDB2MzVfYzAwazEzNSEhIX0=
```

再丟到 base64 decode

`CTF{d3l1c10u5_c00k135!!5n00py_l0v35_c00k135!!!}`

**Flag 3**

response header

`Flag_3: Q1RGe2g3N3BfaDM0ZDNyPz8/MTVfMTdfMzQ3NGKsMz99`

base64 decode

`CTF{h77p_h34d3r???15_17_3474bl3?}`

**Flag 4**

檢測元素的"紀錄"：

```
flag_4 is hidden in somewhere
```

訊息的最右邊有一個 flag.js:5:1

點開來看到這個

```
    flag_4 = ""
    c = "\x9a\x8d\x9f\xa2\xba\xe9\xac\xb5\xbd\x86\xa0\xe9\xac\x86\xab\xea\xaf\xea\xab\xec\xea\x86\xec\xe8\xb4\xa9\xb5\xea\x86\xb3\xec\xe6\xa0\xea\xec\xf5\xa0\xe9\xac\x86\xba\xed\xb7\xf8\xf8\xf8\xa4"
    for (var i = 0; i < c.length; i++){flag_4 += String.fromCharCode(c[i].charCodeAt()^217)}
    //console.log(flag_4)
    console.log("flag_4 is hidden in somewhere")
    flag_4 = ""
```

有個 console.log(flag_4)

google chrome ，有個 console

在裡面貼上這些 code

`CTF{c0uld_y0u_r3v3r53_51mpl3_j5?y35,y0u_c4n!!!}`

<h2 id = "Mission">Mission (Web)</h2>

**Flag 1**

mission1.php：

```
'flag' is a kind of encoding. You should accept that encoding that the web server could give you the flag.
```

用 burp

```
GET /mini_scoreboard_data HTTP/1.1
Host: final.ctf.tw
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.11; rv:43.0) Gecko/20100101 Firefox/43.0
Accept: application/json, text/javascript, */*; q=0.01
Accept-Language: zh-TW,zh;q=0.8,en-US;q=0.5,en;q=0.3
Accept-Encoding: gzip, deflate
X-Requested-With: XMLHttpRequest
Referer: http://final.ctf.tw/dashboard
Cookie: csrftoken=4DJcYObLZm8hn3z3TlleNUJGi76bmWMF; _ga=GA1.3.511832259.1452077703; sessionid=95tccw56q9mvr0pqd6d233yeulf48g6f
Connection: close
If-Modified-Since: Mon, 11 Jan 2016 16:00:24 GMT
```

他說 you should accept that encoding

在 Accept-Encoding 後面加上 flag 再送回去

`CTF{custom_http_header!!!!}`

**Flag 2**

mission2.php：

```
GET to /mission2.php not supported.
```

疑似是在說 mission2.php 不支援 GET

HTTP 的請求方法有

```
OPTIONS, HEAD, GET, POST, PUT, DELETE, TRACE, CONNECT
```

每一種都試著丟回去看看，發現只有 OPTIONS 回傳 200

接著發現檢查元素 -> 網路 -> 檔頭裡面的回應檔頭寫著

```
Allow: "GETFLAG, OPTIONS"
```

把 header 改成 GETFLAG

`CTF{502_not_implement????sent_custom_http_method_instead~}`

**Flag 3**

mission3.php 

```php
 <?php
show_source(__FILE__);

$lv1 = 0; $lv2 = 0; $lv3 = 0;

$a = @$_GET['arg1'];
if (!is_array($a))
{
    $lv1 = 1;
    for ($i = 0; $i < 256; $i++)
        $lv1 &= ord($a[$i]) == $i;
}

$a = @$_GET['arg2'];
if (is_array($a))
{
    $lv2 |= @$a[1] === $a[2];
    $lv3 |= @(!is_numeric($a[0]) && $a[0] >= 217);
}


echo "lv1: $lv1<br>";
echo "lv2: $lv2<br>";
echo "lv3: $lv3<br>";

if ($lv1 && $lv2 && $lv3){
    include "flag.php";
    echo $flag_3;
}
lv1: 0
lv2: 0
lv3: 0
```

最後要讓他 `echo flag_3` 就必須讓 `if` 成立

那麼 `lv1, lv2, lv3` 都必須等於 `1`，做 `AND` 最後得到的值才會是 `1`

先看 lv1

要讓 if 過，arg1 就不能是陣列

要讓 lv1 最後等於 1，必須要讓 for loop 裡面的值都相等

其中 `ord( )` 函數是返回字符串的首個字符的 ASCII 值

所以 arg1 丟進去的值必須是 0~255 的 ASCII

因為是在 url 裡丟參數，所以要先把 0~255 轉成十六進位再轉成 url 表示法

```python
for i in range(256):
    print str(hex(i)).replace("0x", "%")
```

url encode 後面固定用十六進位表示，可以直接把 0x 取代成 %

```
 %00%01%02%03%04%05%06%07%08%09%0A%0B%0C%0D%0E%0F%10%11%12%13%14%15%16%17%18%19%1A%1B%1C%1D%1E%1F%20%21%22%23%24%25%26%27%28%29%2A%2B%2C%2D%2E%2F%30%31%32%33%34%35%36%37%38%39%3A%3B%3C%3D%3E%3F%40%41%42%43%44%45%46%47%48%49%4A%4B%4C%4D%4E%4F%50%51%52%53%54%55%56%57%58%59%5A%5B%5C%5D%5E%5F%60%61%62%63%64%65%66%67%68%69%6A%6B%6C%6D%6E%6F%70%71%72%73%74%75%76%77%78%79%7A%7B%7C%7D%7E%7F%80%81%82%83%84%85%86%87%88%89%8A%8B%8C%8D%8E%8F%90%91%92%93%94%95%96%97%98%99%9A%9B%9C%9D%9E%9F%A0%A1%A2%A3%A4%A5%A6%A7%A8%A9%AA%AB%AC%AD%AE%AF%B0%B1%B2%B3%B4%B5%B6%B7%B8%B9%BA%BB%BC%BD%BE%BF%C0%C1%C2%C3%C4%C5%C6%C7%C8%C9%CA%CB%CC%CD%CE%CF%D0%D1%D2%D3%D4%D5%D6%D7%D8%D9%DA%DB%DC%DD%DE%DF%E0%E1%E2%E3%E4%E5%E6%E7%E8%E9%EA%EB%EC%ED%EE%EF%F0%F1%F2%F3%F4%F5%F6%F7%F8%F9%FA%FB%FC%FD%FE%FF
```

空格要刪掉

再來看 lv2 跟 lv3

首先 arg2 傳進去的型態要是陣列

`if` 裡面是做 `OR`

但 lv2 跟 lv3 預設值都為 0

所以後面的判別式都要為 1，最後的值才能等於 1

`===`的意思是，除了值相等，格式也要相等

```php
$lv3 |= @(!is_numeric($a[0]) && $a[0] >= 217);
```

lv3 比較麻煩一點

a[0] >= 217，沒什麼好討論的

但 `is_numeric(mixed var)` 是判斷變數是否為數字或數字的字串

必須想辦法繞過 (bypass)使他傳回 false 才行

網路上有這篇[繞過文](http://www.hackblog.cn/post/72.html)

總之就是在數字的後面加上任何除了數字之外的字母或符號就可以過了

```
arg2[ ]=217a&arg2[ ]=1&arg2[ ]=1
```

`CTF{you_already_know_how_to_send_GET_and_POST_requests}`

<h2 id = "Login">Login as admin 1 (Web)</h2>

**Flag 1**

/robots.txt

```
User-agent: *
Disallow: /backup/
```

把 /robots.txt 改成 /backup/

出現了一個 backup.zip 的壓縮檔

下載打開後

flag 1 就藏在 index.php 的註解中

<h2 id = "Eve">Eve (forensic)</h2>

**Flag 1**

題目是由 wireshark 錄 pcap 檔

大概知道他在瀏覽網站並且在傳壓縮檔？

其中一個封包有 html code

裡面有一段是這樣的

```
<h1>Flag 1</h1>
    <div class="lead">
        Flag 1 is <code id="flag1"></code><br>
    </div>
```

看來只要執行這個網頁，就可以直接看到 flag 1 了

把網頁抓出來

File -> Export Objects -> HTTP… -> 選擇要抓的那個封包，存成 html 檔

將檔案打開，就得到 flag 1

**Flag 2**

[NetworkMiner](http://www.netresec.com/?page=NetworkMiner) 可以把 wireshark 錄到的內容全部都抓出來，包含檔案（超變態）

Windows, Mac, Linux 都支援，但建議在 Windows，單純只是安裝上比較省事而已

安裝完執行後，直接 file open，把整個 eve.pcap 給丟進去

因為知道第二題是要解壓縮檔，直接點到 files

抓到了七個檔案

隨便點一個按右鍵 -> open folder

index.html 就是第一題抓到的那個網頁

gift.zip 被加密了，網頁上說

```
password: This_is_the_passwr0d_of_zip_it_is_not_the_flag_2
```

貼上去，很好，密碼錯誤、沒有檔案可以解壓縮

只好看另外兩個壓縮檔了

`.par2` 查了一下，大概就是可以修復或再生受損的數據

[QuickPar](http://www.quickpar.org.uk/) 這個程式可以建立 par2 檔

那應該也可以修復壞掉的壓縮檔

安裝完後直接對 gift.zip 點右鍵選擇這個程式啟動

然後點選 open 加入兩個 par2 檔幫助修復

但點開來後沒有這兩個檔案的選項

亂點了半天發現要把兩個 par2 檔的副檔名(.zip) 刪掉，才會出現在選項中

都丟進去後按 Repair

gift.zip 就變成綠色的顯示 Repaired

直接對著他點兩下開啟後輸入 password

就得到 flag 2 了

<h2 id = "What_is_that">What is that (misc)</h2>

下載檔案後是一個 QR code

直接把它截圖成 png 檔

找一個 decode QR code 的網站丟進去

得到 flag

<h2 id = "Large">Large (misc)</h2>

也是一個 QR code

跟上一題的解法完全一樣

<h2 id = "LLARGE">LLARGE (misc)</h2>

又是一個 QR code 

但是丟到網頁上解碼卻得到

```
PK���������4�G�+W�G���H�������flag.txtUT	���g�V�g�Vux��������������H-JU/VH�IL�Rp�q���H�O��K,����LI��̋���O�OIU�������r�=Kԋ��s��2���k����PK�����������4�G�+W�G���H���������������������flag.txtUT����g�Vux�������������PK����������N���������
```

發現 PK 是 zip 檔的 file format 的開頭

發現[這個可以（解析成十六進位）](http://www.onlinebarcodereader.com/) ，[這個也可以（解析成十六進位 + ASCII）](http://online-barcode-reader.inliteresearch.com/default.aspx)

有很多網站解析出來的不是看不懂的東西就是給我 error

上面兩個網頁可以把它轉成十六進位，可愛多了

[010 editor](http://www.sweetscape.com/010editor/) 可以把十六進位轉成壓縮檔

存成 .zip 檔，解壓縮，得到 flag.txt 

<h2 id = "zxcvb">zxcvb (misc)</h2>

```
John doesn't like zxcvb :((
Yp4U1;IKY_XX,dokt"alh"HH.soav+
```

發現 zxcvb 就是鍵盤橫的按過去

某人提示我 Dvorak

查了之後得知是另外一種鍵盤的名稱

用 windows 比較方便，可以直接插入 Dvorak 鍵盤（內建的）

照著打上去就得到 flag 了
