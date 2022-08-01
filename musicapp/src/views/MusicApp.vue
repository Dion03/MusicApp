<template>
  <v-container class="pa-0 white-text" fluid style="padding: 0 !important; ">
    <appBar></appBar>
    <v-row height="100%" style="background: linear-gradient(163deg, rgba(54,10,10,1) 0%, rgba(21,4,4,1) 21%, rgba(0,0,0,1) 69%);">
      <v-col cols="8">
        <v-card class="ml-16 mt-5" flat color="transparent" style="height: 100vh; overflow-y: scroll;">
          <v-card-title style="color: white">Playlist</v-card-title>
          <v-card class="mt-5 songCard" v-for="(song, index) in songs" :key="index" color="transparent">
            <v-list-item dense style="color: white !important;">
              <v-img :src="song.coverAlbum" style="max-width:50px !important; height:50px !important"></v-img>
              <v-list-item-content class="ml-5">
                <v-list-item-title>{{song.songName}}<br/></v-list-item-title>
              </v-list-item-content>
              <v-list-item-content class="ml-5">
                <v-list-item-title>{{song.artist}}<br/></v-list-item-title>
              </v-list-item-content>
              <v-list-item-content class="ml-5">
                <v-list-item-title class="text-lg" >{{song.songLenght}}<br/></v-list-item-title>
              </v-list-item-content>
            </v-list-item>
        </v-card>
        </v-card>
      </v-col>
      <v-col cols="4">
        <musicQueue></musicQueue>
      </v-col>
    </v-row>
    <v-row no-gutters>
      <v-app-bar class="ml-auto mr-auto playbar" dense fixed bottom></v-app-bar>
    </v-row>
  </v-container>
</template>

<script>
// import axios from 'axios'
  import appBar from '@/components/MusicAppBar'
  import musicQueue from '@/components/musicQueue'

  export default {
    name: 'MusicApp',
    components:{appBar, musicQueue},

    data: () => ({
      songs: [
        {
          id: 1,
          artist: 'Tom Rosenthal',
          songName: "Now You Know" ,
          songUrl: "https://upload.wikimedia.org/wikipedia/commons/1/1e/Tom_Rosenthal_%28Musician%29.jpg",
          coverAlbum: "https://i.scdn.co/image/ab67616d0000b2734523edea415c3ddb92d3a34c",
          songLenght: '3:33'

        },
        {
          id: 2,
          artist: 'Tom Rosenthal',
          songName: "Worries" ,
          songUrl: "https://upload.wikimedia.org/wikipedia/commons/1/1e/Tom_Rosenthal_%28Musician%29.jpg",
          coverAlbum: "https://i1.sndcdn.com/artworks-kWZFmkkpHKWw-0-t500x500.jpg",
          songLenght: '2:10'

        },
        {  
          id: 3,
          artist: 'Patrick Watson',
          songName: "Je te laisserai des mots" ,
          songUrl: "https://upload.wikimedia.org/wikipedia/commons/1/1e/Tom_Rosenthal_%28Musician%29.jpg",
          coverAlbum: "https://i.scdn.co/image/ab67616d0000b27339372cb9fc75f395a5090a8d",
          songLenght: '2:40'

        },    
        {  
          id: 4,
          artist: 'Patrick Watson',
          songName: "Lost With You" ,
          songUrl: "https://upload.wikimedia.org/wikipedia/commons/1/1e/Tom_Rosenthal_%28Musician%29.jpg",
          coverAlbum: "https://i1.sndcdn.com/artworks-kmUz33al9hrk-0-t500x500.jpg",
          songLenght: '2:55'

        }, 
        {
          id: 5,
          artist: 'Edith Wiskers',
          songName: "It's Ok (cover)" ,
          songUrl: "https://upload.wikimedia.org/wikipedia/commons/1/1e/Tom_Rosenthal_%28Musician%29.jpg",
          coverAlbum: "https://cdns-images.dzcdn.net/images/cover/b78d0f72ee55ffaf69f625c2afee260e/200x200.jpg",
          songLenght: '3:34'

        },
                {
          id: 6,
          artist: 'Edith Wiskers',
          songName: "Home" ,
          songUrl: "https://upload.wikimedia.org/wikipedia/commons/1/1e/Tom_Rosenthal_%28Musician%29.jpg",
          coverAlbum: "https://cdns-images.dzcdn.net/images/cover/98ee2fb23e1f5776a3b093ea25ee0255/500x500.jpg",
          songLenght: '3:17'

        },
        {
          id: 7,
          artist: 'Coldplay',
          songName: "Trouble" ,
          songUrl: "https://upload.wikimedia.org/wikipedia/commons/1/1e/Tom_Rosenthal_%28Musician%29.jpg",
          coverAlbum: "https://upload.wikimedia.org/wikipedia/en/thumb/e/e2/Trouble_cover_art.jpg/220px-Trouble_cover_art.jpg",
          songLenght: '4:33'

        },
                {
          id: 8,
          artist: 'Coldplay',
          songName: "Yellow" ,
          songUrl: "https://upload.wikimedia.org/wikipedia/commons/1/1e/Tom_Rosenthal_%28Musician%29.jpg",
          coverAlbum: "https://upload.wikimedia.org/wikipedia/en/9/9b/Yellow_cover_art.JPG",
          songLenght: '4:26'

        },
        {
          id: 9,
          artist: 'Tom Odell',
          songName: "Heal" ,
          songUrl: "https://upload.wikimedia.org/wikipedia/commons/1/1e/Tom_Rosenthal_%28Musician%29.jpg",
          coverAlbum: "https://i1.sndcdn.com/artworks-000271046855-s5su2s-t500x500.jpg",
          songLenght: '3:13'

        },
                {
          id: 10,
          artist: 'Tom Odell',
          songName: "Best Day Of My Life" ,
          songUrl: "https://upload.wikimedia.org/wikipedia/commons/1/1e/Tom_Rosenthal_%28Musician%29.jpg",
          coverAlbum: "https://i1.sndcdn.com/artworks-31vnQOi1ScrL-0-t500x500.png",
          songLenght: '2:26'
        },
      ]    
      }),

    methods:{
      

    }
  }
</script>
<style>
.playbar{
  background-color: rgba(45, 44, 45, 0.5) !important; 
  height: 12.5vh !important; 
  width: 80%; 
  border-top-left-radius: 1em !important;
  border-top-right-radius: 1em !important;
}
.songCard:hover{
  background-color: rgba(66, 66, 66, 0.5) !important;
}
</style>

<!-- https://ws.audioscrobbler.com/2.0/?method=user.getTopArtists&user=D_boom&api_key=2e7d613dddaf284a1f89bbc37b835efe&limit=10&format=json&callback=? -->