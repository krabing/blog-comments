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

---    
 
**如果系统没有安装ffmpeg，按照下面步骤安装。（以Centos7.5为例）<p>
方案一：用yum安装<p>**
由于CentOS自带的yum库不包含ffmpeg软件包，因此借助第三方yum源下载ffmpeg。<p>

1.升级yum
```
[root@dev01 ~]#sudo yum install epel-release -y
[root@dev01 ~]#sudo yum update -y
```
2.安装Nux Dextop Yum 源
```
[root@dev01 ~]#sudo rpm --import http://li.nux.ro/download/nux/RPM-GPG-KEY-nux.ro
[root@dev01 ~]#sudo rpm -Uvh http://li.nux.ro/download/nux/dextop/el7/x86_64/nux-dextop-release-0-5.el7.nux.noarch.rpm
```
3.安装FFmpeg 和 FFmpeg开发包
```
[root@dev01 ~]#sudo yum install ffmpeg ffmpeg-devel -y
```
4.测试
```
[root@dev01 ~]#ffmpeg -version
ffmpeg version 2.8.15 Copyright (c) 2000-2018 the FFmpeg developers
built with gcc 4.8.5 (GCC) 20150623 (Red Hat 4.8.5-36)
configuration: --prefix=/usr --bindir=/usr/bin --datadir=/usr/share/ffmpeg --incdir=/usr/include/ffmpeg --libdir=/usr/lib64 --mandir=/usr/share/man --arch=x86_64 --optflags='-O2 -g -pipe -Wall -Wp,-D_FORTIFY_SOURCE=2 -fexceptions -fstack-protector-strong --param=ssp-buffer-size=4 -grecord-gcc-switches -m64 -mtune=generic' --extra-ldflags='-Wl,-z,relro ' --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libvo-amrwbenc --enable-version3 --enable-bzlib --disable-crystalhd --enable-gnutls --enable-ladspa --enable-libass --enable-libcdio --enable-libdc1394 --enable-libfdk-aac --enable-nonfree --disable-indev=jack --enable-libfreetype --enable-libgsm --enable-libmp3lame --enable-openal --enable-libopenjpeg --enable-libopus --enable-libpulse --enable-libschroedinger --enable-libsoxr --enable-libspeex --enable-libtheora --enable-libvorbis --enable-libv4l2 --enable-libx264 --enable-libx265 --enable-libxvid --enable-x11grab --enable-avfilter --enable-avresample --enable-postproc --enable-pthreads --disable-static --enable-shared --enable-gpl --disable-debug --disable-stripping --shlibdir=/usr/lib64 --enable-runtime-cpudetect
libavutil      54. 31.100 / 54. 31.100
libavcodec     56. 60.100 / 56. 60.100
libavformat    56. 40.101 / 56. 40.101
libavdevice    56.  4.100 / 56.  4.100
libavfilter     5. 40.101 /  5. 40.101
libavresample   2.  1.  0 /  2.  1.  0
libswscale      3.  1.101 /  3.  1.101
libswresample   1.  2.101 /  1.  2.101
libpostproc    53.  3.100 / 53.  3.100
```
