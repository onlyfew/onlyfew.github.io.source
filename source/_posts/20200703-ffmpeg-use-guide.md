---
title: 【技术】FFMPEG命令备忘
date: 2020-07-02 21:21
tags: [技术, FFMPEG, 音视频, 使用指南]
categories: 技术
---
## FFMPEG基础介绍
//todo
## FFMPEG命令备忘
- 将MP4转为m3u8，16秒为一个片段
```
ffmpeg -i ./20200701.mp4 -c:v libx264 -hls_time 16 -hls_list_size 0 -c:a aac -strict -2 -f hls ./20200701.m3u8
```
<!-- more -->
- 下载m3u8并合成为mp4
```
ffmpeg -i "https://yimiyuedu-online.oss-cn-beijing.aliyuncs.com/teacher/a4841c01604a8efc872f4d9040bca45e_121220554827893760.m3u8" -vcodec copy -acodec copy -absf aac_adtstoasc ./100604.mp4
```
- 下载m3u8只保留音频aac
```
ffmpeg -i "https://yimiyuedu-online.oss-cn-beijing.aliyuncs.com/teacher/a4841c01604a8efc872f4d9040bca45e_121220554827893760.m3u8" -c:a copy -vn ./b.aac
```
- 将aac格式转换为wav格式
```
ffmpeg -i b.aac c.wav
```
- 剪切指定时间段的音频单独保存，-ss为起始时间，-t为持续多长时间 -to代表截止时间
```
ffmpeg -ss 00:26:00 -t 00:02:00 -i c.wav d.wav
```
- 从指定mp4视频中截取3段并拼接成一段mp4
```
#先剪切出三端
ffmpeg  -i ./20200630.mp4 -vcodec copy -acodec copy -ss 04:20:30 -to 04:22:00 ./20200630-1.mp4
ffmpeg  -i ./20200630.mp4 -vcodec copy -acodec copy -ss 04:23:40 -to 04:33:00 ./20200630-2.mp4
ffmpeg  -i ./20200630.mp4 -vcodec copy -acodec copy -ss 04:35:00 -to 04:37:22 ./20200630-3.mp4
#将三段转换为ts片段
ffmpeg -i ./20200630-1.mp4 -c copy -bsf:v h264_mp4toannexb -f mpegts ./20200630-1.ts
ffmpeg -i ./20200630-2.mp4 -c copy -bsf:v h264_mp4toannexb -f mpegts ./20200630-2.ts
ffmpeg -i ./20200630-3.mp4 -c copy -bsf:v h264_mp4toannexb -f mpegts ./20200630-3.ts
#将片段拼接为视频
ffmpeg -i "concat:20200630-1.ts|20200630-2.ts|20200630-3.ts" -c copy -bsf:a aac_adtstoasc -movflags +faststart 20200630-cuiyong.mp4
```
- 