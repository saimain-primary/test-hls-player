<script>
import fluidPlayer from "fluid-player";
export default {
  name: "FluidPlayer",
  props: {},
  data() {
    return {
      player: null,
    };
  },
  mounted() {
    this.player = fluidPlayer(this.$refs.myVideoPlayer, {
      layoutControls: {
        primaryColor: "#0000ff",
        playButtonShowing: false,
        playPauseAnimation: false,
        fillToContainer: true,
        autoPlay: true,
        preload: true,
        mute: true,
        doubleclickFullscreen: false,
        subtitlesEnabled: false,
        keyboardControl: false,
        layout: "default",
        allowDownload: false,
        playbackRateEnabled: true,
        allowTheatre: false,
        loop: false,
        controlBar: {
          autoHide: true,
          autoHideTimeout: 3,
          animated: true,
          playbackRates: ["x2", "x1.5", "x1", "x0.5"],
        },
        timelinePreview: {},
        htmlOnPauseBlock: {
          html: null,
          height: null,
          width: null,
        },
        playerInitCallback: function () {},
        miniPlayer: {
          enabled: true,
          width: 400,
          height: 225,
        },
      },
    });
  },
  destroyed() {
    if (!this.player) {
      return;
    }

    this.player.destroy();
  },
};
</script>

<template>
  <div class="fluid-component">
    <!-- <video ref="myVideoPlayer">
      <source
        src="https://cdn.fluidplayer.com/videos/valerian-1080p.mkv"
        data-fluid-hd
        title="1080p"
        type="video/mp4"
      />
    </video> -->

    <video id="hls-video" ref="myVideoPlayer">
      <source
        src="https://atom1.apaas.com.mm/vod/Hollywood_Movies/2023/July/Week2/Bhoothnath_Returns_2014/playlist.m3u8"
        type="application/x-mpegURL"
      />
    </video>
    <!-- <video id="hls-video" ref="myVideoPlayer">
      <source
        src="https://live-par-1-abr-cdn.livepush.io/live/bigbuckbunnyclip/index.m3u8"
        type="application/x-mpegURL"
      />
    </video> -->
    <!-- <video id="hls-video" ref="myVideoPlayer">
      <source
        src="https://atom1liveacc.apaas.com.mm/mrtv4livecp1/index.m3u8"
        type="application/x-mpegURL"
      />
    </video> -->
  </div>
</template>

<style>
@import "fluid-player/src/css/fluidplayer.css";

div.fluid-component,
div.fluid-component > video {
  width: 100%;
  height: 100%;
}
</style>