<template>
  <v-app-bar class=" playbar" dense fixed bottom>
    <v-row class="mt-7 justify-center" width="500px" style="width: 750px !important">
    <v-col cols="2"><h4 style="color:white">{{this.currentSong.songName}} - {{this.currentSong.artist}}</h4></v-col>
      <v-col cols="8" class="d-flex justify-center">
        <v-btn icon @click="toggleShuffle">
          <v-icon large color="#c23a3a" v-if="this.shuffle">mdi-shuffle</v-icon>
          <v-icon large color="white" v-else>mdi-shuffle</v-icon>
        </v-btn>
        <v-btn icon @click="stopSong">
          <v-icon  class="PlayIcons">mdi-stop</v-icon>
        </v-btn>
        <v-btn icon style="border: 1px solid white" @click="playSong">
          <v-icon class="PlayIcons">mdi-play</v-icon>
        </v-btn>
        <v-btn icon @click="pauseSong">
          <v-icon  class="PlayIcons">mdi-pause</v-icon>
        </v-btn>
        <v-btn icon @click="toggleLoop">
          <v-icon large color="#c23a3a" v-if="this.loop">mdi-repeat</v-icon>
          <v-icon large color="white" v-else>mdi-repeat</v-icon>
        </v-btn>
      </v-col>
      <v-col cols="2">
        <v-slider class="mt-2 text-white" :prepend-icon="VolumeIcon" style="color: white !important" v-model="volume" @input="updateVolume(volume)" max="1" step="0.1" @click:prepend="toggleMute"></v-slider>
        <template v-slot:prepend-icon>
    <v-icon color="red">{{this.VolumeIcon}}</v-icon>
  </template>
      </v-col>
    </v-row>
  </v-app-bar>
</template>
<script>
import {Howler} from 'howler'
export default {
    name: 'Play-bar',
    props:{
      loop: Boolean,
      shuffle: Boolean,
      currentSong: Object
    },
    data(){
      return{
        volume: 0.5,
        muted: false,
        VolumeIcon: "mdi-volume-high"
      }
    },
  methods: {
    playSong(index) {
      this.$emit('playsong', index)
    },
    pauseSong() {
      this.$emit('pausesong')
    },
    stopSong() {
      this.$emit('stopsong')
    },
    updateVolume (volume) {
      Howler.volume(volume)
    },
    toggleMute () {
      Howler.mute(!this.muted)
      this.muted = !this.muted
      if(this.VolumeIcon == "mdi-volume-high")
      {
        this.VolumeIcon = "mdi-volume-mute"
      }else{
        this.VolumeIcon = "mdi-volume-high"
      }
    },
    toggleLoop () {
      this.$emit('toggleloop', !this.loop)
    },
    toggleShuffle () {
      this.$emit('toggleshuffle', !this.shuffle)
    }
  },
}
</script>
