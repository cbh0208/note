# ffprobe 

- 用于查看媒体文件头信息的工具 



# ffplay 

- 用于播放媒体文件的工具 





# ffmpeg

##### 流处理

```swift
ffmpeg -i input.mp4 -c:v libx264 -c:a aac -strict -2 -f hls output.m3u8
```

```
ffmpeg -i input.mp4 -c:v libx264 -c:a aac -hls_time 5 -hls_list_size 0  -strict -2 -f hls out.m3u8
```

##### 字幕

```
ffmpeg -i video.mkv -an -vn -scodec copy sub3.ass

ffmpeg -i video.mkv -vcodec copy -acodec copy -sn video-no-subs.mkv
```

