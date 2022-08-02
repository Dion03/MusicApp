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
              <v-img :src="song.coverAlbum" class="queueImg" style="max-width: 50px !important;"></v-img>
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
<style scoped src="@/assets/css/style.css"></style>
