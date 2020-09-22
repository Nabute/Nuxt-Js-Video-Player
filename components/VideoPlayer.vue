<template>
  <div class="vjs-custom-skin">
    <video ref="videoPlayer" class="video-js"></video>
  </div>
</template>

<script>
import videojs from "video.js";
export default {
  name: "VideoPlayer",
  props: {
    options: {
      type: Object,
      default() {
        return {};
      },
    },
  },
  data() {
    return {
      player: null,
    };
  },
  mounted() {
    this.player = videojs(
      this.$refs.videoPlayer,
      this.options,
      function onPlayerReady() {
        console.log("onPlayerReady", this);
      }
    );
  },
  beforeDestroy() {
    if (this.player) {
      this.player.dispose();
    }
  },
};
</script>


<style>
.vjs-custom-skin {
  width: 100%;
  color: #ffffff !important;
}

.vjs-custom-skin > .video-js {
  width: 100%;
  min-height: 670px;
  font-family: "PingFang SC", "Helvetica Neue", "Hiragino Sans GB", "Segoe UI",
    "Microsoft YaHei", "微软雅黑", sans-serif;
}

.vjs-custom-skin > .video-js .vjs-play-progress,
.vjs-custom-skin > .video-js .vjs-volume-level {
  background-color: #ffffff !important;
}

.vjs-custom-skin > .video-js .vjs-loading-spinner {
  border-color: #ffffff !important;
}

.video-js:hover .vjs-big-play-button,
.vjs-custom-skin > .video-js .vjs-big-play-button:focus,
.vjs-custom-skin > .video-js .vjs-big-play-button:active {
  background-color: #ffffff !important;
}
</style>