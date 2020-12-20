<template>
<!--  <div class="row flex flex-center q-pb-md q-pt-md">-->
  <div class="row items-center">
    <div id="wavesurfer"></div>
<!--    <q-btn-->
<!--      id="detailButton"-->
<!--      color="white"-->
<!--      flat-->
<!--      round-->
<!--      icon="switch-toggle"/>-->
    <q-expansion-item
      switch-toggle-side
      expand-separator
    >
    <!--  这中间填充页面内容  -->
    </q-expansion-item>
    <div id="musicInfo">

    </div>
    <q-btn
      id="playButton"
      color="white"
      outline
      round
      icon="play_arrow"
      size="12px"
      @click="wavesurfer.playPause()"
    />
  </div>
</template>

<script>
  import WaveSurfer from "wavesurfer.js"

  export default {
    name: "Player",
    data() {
      return {
        wavesurfer: null,
        url: '~assets/music/ShineOverMe.mp3'
      }
    },
    //async异步处理，看看data中的wavesurfer有没有初始化好
    //如果没有，则初始化wavesurfer对象
    mounted() {
      if (!this.wavesurfer) {
        this.createWaveSurfer();
      }
    },
    methods: {
      createWaveSurfer() {
        this.wavesurfer = WaveSurfer.create({
          container: "#wavesurfer",
          barWidth: 3
        });
        this.load();
        this.wavesurfer.on('error', error => {
          console.log(error)
        })
      },
      //使用wavesurfer中的load方法必须要require（url），不然会报错
      load() {
        this.wavesurfer.load(require('assets/music/ShineOverMe.mp3'))
      },

    }
  }
</script>

<style scoped>
  #wavesurfer {
    display: none;
  }

  #detailButton {

  }

  #musicInfo {

  }

  #playButton {

  }
</style>
