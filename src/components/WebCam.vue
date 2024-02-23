<template>
  <div>
    <video ref="video" @canplay="initCanvas()">Stream Unavailable</video>
    <v-btn @click="startCapture()">Open Camera</v-btn>
    <canvas ref="canvas" style="display: none" />
    <v-btn @click="capture()">Capture</v-btn>
  </div>
</template>

<script>
export default {
  name: "WebCam",
  mounted() {
    this.canvas = this.$refs.canvas;
    this.video = this.$refs.video;
  },
  methods: {
    startCapture() {
      navigator.mediaDevices
        .getUserMedia({ video: true, audio: false })
        .then((stream) => {
          this.video.srcObject = stream;
          this.video.play();
        })
        .catch((error) => {
          console.log(error);
        });
    },
    capture() {
      let context = this.canvas.getContext("2d");
      context.drawImage(
        this.video,
        0,
        0,
        this.video.videoWidth,
        this.video.videoHeight
      );
      this.$emit("captured", this.canvas.toDataURL("image/png"));
    },
    initCanvas() {
      this.canvas.setAttribute("width", this.video.videoWidth);
      this.canvas.setAttribute("height", this.video.videoHeight);
    },
  },
  data() {
    return {
      video: null,
      canvas: null,
    };
  },
};
</script>

<style scoped></style>
