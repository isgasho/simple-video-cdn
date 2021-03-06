# Simple Video CDN
A minimal CDN for load balance studies purposes.

![Architecture](/images/architecture.png)


#### Docker services

- *simple-video-cdn_origin_1:* packager/origin
- *simple-video-cdn_cache_1:* cache server 1
- *simple-video-cdn_cache_2:* cache server 2
- *simple-video-cdn_lb_1:* load balancer


## Running

#### Delivery
Delivery HLS and Dash video (two cache instances):
```bash
make run
```


#### Ingest
- Ingest 10 seconds of the clip 'Big Buck Bunny':
```bash
make ingest
```

Or ingest another video to http://0.0.0.0:8080/ingest/bbb.

#### Consume
- Consume the HLS playlist:
```bash
curl -s http://0.0.0.0:8080/live/hls/bbb/index.m3u8
```
- Consume the Dash play list:
```bash
curl -s http://0.0.0.0:8080/live/dash/bbb/index.mpd
```

## Built With
- [ffmpeg](https://github.com/FFmpeg/FFmpeg) - audio/video handler
- [nginx](https://github.com/nginx/nginx) - HTTP server and reverse proxy
- [nginx-ts-module](https://github.com/arut/nginx-ts-module) - receives MPEG-TS and serves HLS and DASH over HTTP
- [Lua](https://www.lua.org/) - script language

## Authors
Ana Carolina Castro - Initial work - Globo.com

## Acknowledgments
This is not a resilient architecture.