<template>
      <v-col cols="8">
        <v-card class="ml-16 mt-5" flat color="transparent" style="height: 100vh; overflow-y: scroll;">
          <v-card-title style="color: white">Playlist</v-card-title>
          <v-card class="mt-5 songCard" v-for="(song, index) in playlist" :key="index" color="transparent" @dblclick="playSong()">
            <v-list-item dense style="color: white !important;" @click="selectTrack(song)"  :class="[{selected: song === selectedSong}]">
              <v-img :src="song.coverAlbum" style="max-width:50px !important; height:50px !important"></v-img>
              <v-list-item-content class="ml-5">
                <v-list-item-title class="textLG">{{song.songName}}<br/></v-list-item-title>
              </v-list-item-content>
              <v-list-item-content class="ml-5">
                <v-list-item-title class="textLG">{{song.artist}}<br/></v-list-item-title>
              </v-list-item-content>
              <v-list-item-content class="ml-5">
                <v-list-item-title class="textLG">{{ Math.round(song.howl.duration())  }} sec<br/></v-list-item-title>
              </v-list-item-content>
            </v-list-item>
        </v-card>
        </v-card>
      </v-col>
</template>

<script>
// import axios from 'axios'

  export default {
    name: 'Play-list',
    props: {
      playlist: Array,
      selectedSong: Object
    },
    data: () => ({
   
      }),

methods: {
  selectTrack (track) {
    this.$emit('songSelec', track)
  },
  playSong(index) {
    this.$emit('playsong', index)
  },
}
  }
</script>
<style scoped src="@/assets/css/style.css"></style>
