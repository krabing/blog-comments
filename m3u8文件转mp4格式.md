1. m3u8文件可以做为文本打开，可以看到里面存储着每一个片段的绝对路径。如果路径不对，需要修改替换为正确的路径。

```
[xiebin@dev01 ~]$ cat xxx.m3u8
#EXTM3U
#EXT-X-VERSION:3
#EXT-X-TARGETDURATION:8
#EXT-X-MEDIA-SEQUENCE:0
#EXTINF:4.000000,
/storage/896D-1F02/Android/data/com.UCMobile/files/UCDownloads/VideoData//94bad5572f90065418914b4481bf7d1ae19403dc/Y2hlbmppbmdjb25n0
#EXTINF:6.360000,
/storage/896D-1F02/Android/data/com.UCMobile/files/UCDownloads/VideoData//94bad5572f90065418914b4481bf7d1ae19403dc/Y2hlbmppbmdjb25n1
#EXTINF:4.000000,
/storage/896D-1F02/Android/data/com.UCMobile/files/UCDownloads/VideoData//94bad5572f90065418914b4481bf7d1ae19403dc/Y2hlbmppbmdjb25n2
#EXTINF:2.080000,
```
2. 用ffmpeg命令转码
```
[xiebin@dev01 ~]$ffmpeg -allowed_extensions ALL -i XXX.m3u8 -c copy aaa.mp4
```
