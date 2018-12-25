# 2016 AIS3 pre-exam

* [Web 1](#web1)
* [Web 2](#web2)
* [Crypto 1](#Crypto1)
* [Misc 2](#Misc2)

<h2 id = "web1">Web 1</h2>

/robots.txt

<h2 id = "web2">Web 2</h2>

因為沒有 die 或 exit，所以可以直接利用 curl 取得 body 資訊

- cURL : Linux 工具，c 是 crawl，意旨把網頁抓下來 ([參考](http://blog.masterstudio101.com/2013/05/12/cURL%20%E6%8C%87%E4%BB%A4%E6%95%99%E5%AD%B8%20%28cURL%20command%20how-to%29))
- nc : Linux 工具，Netcat
- telnet : 傳輸協定，以明碼傳輸資料，有時候會被 ssh 取代

所以

curl 可以忽略 header 直接抓 body 資料 (pull)

nc 還是要經過 header 取得 body 資料 (connect)

<h2 id = "Crypto1">Crypto 1</h2>

用 xortool

工具介紹

```
xortool
A tool to do some xor analysis:
- guess the key length (based on count of equal chars)
- guess the key (base on knowledge of most frequent char)
```

```
Usage:
  xortool [-x] [-m MAX-LEN] [FILE]
  xortool [-x] [-l LEN] [-c CHAR | -b | -o] [FILE]
  xortool [-x] [-m MAX-LEN| -l LEN] [-c CHAR | -b | -o] [FILE]
  xortool [-h | --help]
  xortool --version
```

```
Options:
  -x --hex                          input is hex-encoded str
  -l LEN, --key-length=LEN          length of the key
  -m MAX-LEN, --max-keylen=MAX-LEN  maximum key length to probe [default: 65]
  -c CHAR, --char=CHAR              most frequent char (one char or hex code)
  -b --brute-chars                  brute force all possible most frequent chars
  -o --brute-printable              same as -b but will only check printable chars
  -h --help                         show this help
```

```
Examples:
  xortool file.bin
  xortool -l 11 -c 20 file.bin
  xortool -x -c ' ' file.hex
```

```
$ xortool crypto1
The most probable key lengths:
   1:   10.6%
   3:   12.7%
   6:   11.6%
   9:   9.7%
  13:   13.7%
  15:   7.8%
  18:   6.9%
  21:   6.1%
  26:   8.1%
  39:   12.7%
Key-length can be 3*n
Most possible char is needed to guess the key!
```

試試看長度 13

```
$ xortool crypto1 -l 13 -c ' '
4 possible key(s) of length 13:
YPt30Xd_5enat
YPt30X__5enat
YP_30Xd_5enat
YP_30X__5enat
Found 0 plaintexts with 95.0%+ printable characters
See files filename-key.csv, filename-char_used-perc_printable.csv
```

Found 0 plaintext

長度 39

```
1 possible key(s) of length 39:
ais3{XoR_enCrYPtiON_15_n0t_a_G00d_i!ea}
Found 1 plaintexts with 95.0%+ printable characters
See files filename-key.csv, filename-char_used-perc_printable.csv
```

`ais3{XoR_enCrYPtiON_15_n0t_a_G00d_i!ea}`

自己把 ! 改成 d

`ais3{XoR_enCrYPtiON_15_n0t_a_G00d_idea}`

<h2 id = "Misc2">Misc 2</h2>

只是想看檔頭

```
$ xxd -l 128 UNPACK_ME
```

```
 0000000: 375a bcaf 271c 0003 97fa 34cd bf75 0400  7Z..'.....4..u..
 0000010: 0000 0000 2400 0000 0000 0000 0f6d 9320  ....$........m.
 0000020: 7fc7 1bd6 3232 8b34 c4a3 bda1 35ff 1bfe  ....22.4....5...
 0000030: 7606 9e02 4b37 0f8a 77d6 0fba c7d4 3364  v...K7..w.....3d
 0000040: 71f1 cc64 a788 ee07 1d2e 4e63 da79 3394  q..d......Nc.y3.
 0000050: 9dc3 16d0 e647 7f52 b7a1 647c fbc4 2742  .....G.R..d|..'B
 0000060: 8e22 2d36 6608 bb4a ce54 68eb c037 efd2  ."-6f..J.Th..7..
 0000070: c22d 25a9 f93f 64f2 2858 0884 04ea 3691  .-%..?d.(X....6.
```

是 7zip 檔，但是檔頭有錯，z 要小寫，所以解壓縮才會發生 error

移駕到 windows

用 010editor 把 第一行的 5A 改成 7A，檔頭就變回 7z，可以正常解壓縮

```
$ 7z x UNPACK_ME
```

獲得兩個檔案，一個又是檔頭有錯的壓縮檔，一個是他的密碼

接著就進入改檔頭解壓縮的無限迴圈

這時候肯定是要寫一個 script 去跑才是正常的解法

可惜我還不會寫 script

用堅定的意志手動改檔頭複製密碼解壓縮持續了兩個小時

然後我就放棄了。

