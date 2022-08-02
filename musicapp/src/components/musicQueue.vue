<template>
    <v-card class="mt-5 mr-16 queueCard" flat>
        <v-card-title class="textWhite">Queue</v-card-title>
        <v-card-subtitle class="textWhite">Just a list, no functionatality</v-card-subtitle>
        <v-card class="songCard" v-for="(song, index) in playlist" :key="index" color="transparent">
            <v-list-item dense style="color: white !important;">
              <v-list-item-avatar>
                <v-avatar color="dark" size="36">
                  <span>0{{index+1}}</span>
                </v-avatar>
              </v-list-item-avatar>
              <v-img :src="song.coverAlbum" class="queueImg"></v-img>
              <v-list-item-content class="ml-5">
                <v-list-item-title>{{song.songName}}<br/></v-list-item-title>
                <v-list-item-subtitle style="color: white !important;">{{song.artist}}</v-list-item-subtitle>
              </v-list-item-content>
            </v-list-item>
        </v-card>
    </v-card>
</template>

<script>
export default {
  props:{
    playlist: Array
  },
    data: () => ({
    }),
}
</script>

<style>
::-webkit-scrollbar {
    width: 0px;
    background: transparent; /* make scrollbar transparent */
}
.songCard:hover{
  background-color: rgba(66, 66, 66, 0.5) !important;
}
.queueCard{
  background-color: #101111 !important; 
  height: 80%; 
  overflow-y: scroll;
  border-radius: 1em !important;
}
.queueImg{
  max-width:50px !important; 
  height:50px !important
}
.textWhite{
  color: white;
}
</style>