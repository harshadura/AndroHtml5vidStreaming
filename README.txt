== README ==
Video Streaming playback on Android HTML5 Application.
---------------------------------------------------------

Dependencies:
1) JW player - only player that i found which supports Android streaming playback on html5 apps
2) Wowza Streaming engine

Notes:
I have tested a lot about video Streaming behaviour on Android JB version, but seems Android has very less support for HTML5 video streaming.

Method1, Method2 works with Chrome
Method1 works all browsers on Android JB including WebView embed app.

Links:
1) support.jwplayer.com/customer/portal/questions/5496622-streaming-on-android
2) http://support.jwplayer.com/customer/portal/questions/5496622-streaming-on-android

----------
Sample code: Method1
----------

<!DOCTYPE html>
<html>

<head>
<script src="http://p.jwpcdn.com/6/8/jwplayer.js"></script>
</head>

<body>

<center><div id='container'></div></center>

<script>
    jwplayer("container").setup({
		image: "http://content.bitsontherun.com/thumbs/gSzpo2wh-480.jpg",
        file: "http://192.168.1.160:1935/vod/mp4:sample.mp4/playlist.m3u8",
        type: "mp4",
        primary: "html5"
    });
</script>

<hr/>

<div id="player"><a href="rtsp://192.168.1.160:1935/vod/mp4:sample.mp4">Play stream</a></div>

<script type="text/javascript">
	jwplayer("player").setup({
		sources: [{
			file: "rtmp://192.168.1.160:1935/vod/mp4:sample.mp4"
		},{
			file: "http://192.168.1.160:1935/vod/sample.mp4/playlist.m3u8"
		},{
			file: "rtsp://192.168.1.160:1935/vod/sample.mp4"
		}],
		rtmp: {
			bufferlength: 6
		},
		fallback: false
	});
</script>

</body>
</html>