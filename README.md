# rtsp
rtsp 本地视频转视频流，并在web上播放
前端web使用node 后端使用go语言 推流使用ffmpeg

### 1. 环境准备
安装node npm golang ffmpeg
```shell
npm i rtsp2web
```

### 2. 启动服务
```shell
node rtsp2web/example/index.js
```

### 3. 访问页面,
浏览器里打开 rtsp/rtsp2web/example/index-flv.html

### 4. 启动rtsp服务
```shell
cd rtspserver
go run main.go
```

### 5. 启动推流服务，向rtsp服务推流
```shell
# /Users/xxx/Desktop/21M.mp4 替换为你本地的文件
ffmpeg -re  -stream_loop -1 -i  /Users/xxx/Desktop/21M.mp4  -vcodec copy -rtsp_transport tcp -f rtsp rtsp://127.0.0.1:8554/live.sdp
```