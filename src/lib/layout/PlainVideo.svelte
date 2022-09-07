<script>
	export let videourl;

    let videoElement;
    let sentProgress25Event = false;

    function pushVideoEvent(action, percent, currentTime) {
        if (!window.dataLayer)
            return;
        window.dataLayer.push({
            event: "video",
            video_action: action,
            video_percent: percent,
            video_current_time: currentTime,
            video_duration: 77,
            video_title: "How Census will Work"
        });
    }

    function onVideoPlay(event) {
        if (videoElement.currentTime != 0)
            return;
        pushVideoEvent("start", 0, 0);
    }

    function onVideoEnded(event) {
        let t = videoElement.currentTime;
        pushVideoEvent("complete", 100, t);
    }

    function onTimeUpdate(event) {
        if (sentProgress25Event)
            return;
        let t = videoElement.currentTime;
        if (t >= 19.2) {
            sentProgress25Event = true;
            pushVideoEvent("progress", 25, t);
        }
    }
</script>

<style>
    .img-filler-img {
        padding-top: 30px;
        padding-left: 0;
        padding-right: 0;
    }
    video {
        width: 100%;
    }
</style>

<div class="img-filler-img">
  <video
        bind:this={videoElement}
        preload="metadata"
        controls
        on:play={onVideoPlay}
        on:ended={onVideoEnded}
        on:timeupdate={onTimeUpdate}
        >
    <source src="{videourl}" type="video/mp4">
    Your browser does not support the video tag.
  </video>
</div>
