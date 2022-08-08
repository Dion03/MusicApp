<template>
  <v-container class="pa-0 white-text" fluid style="padding: 0 !important; ">
    <appBar></appBar>
    <v-row height="100%" style="background: linear-gradient(163deg, rgba(54,10,10,1) 0%, rgba(21,4,4,1) 21%, rgba(0,0,0,1) 69%);">
      <Playlist @playsong="playSong" :playlist="songs" :selectedSong="selectedSong" @songSelec="selectTrack"></Playlist>
      <v-col cols="4">
        <musicQueue :playlist="songs"></musicQueue>
      </v-col>
    </v-row>
    <v-row no-gutters>
      <Play-Bar
        :currentSong="currentTrack"
        :loop="loop"
        :shuffle="shuffle"
        @playsong="playSong"
        @toggleloop="loopSong"
        @pausesong="pauseSong"
        @toggleshuffle="toggleShuffle"
        @stopsong="stopSong">
      </Play-Bar>
    </v-row>
  </v-container>
</template>

<script>
import {Howl} from 'howler'
import appBar from '@/components/MusicAppBar'
import PlayBar from '@/components/playBar'
import musicQueue from '@/components/musicQueue'
import Playlist from '@/components/Playlist.vue'
export default {
  name: 'MusicApp',
  components:{ appBar, musicQueue, Playlist, PlayBar },
  data: () => ({
    selectedSong: null,
    index: 0,
    playing: false,
    loop: false,
    shuffle: false,
    songs: [
      {
        id: 1,
        artist: 'Tom Rosenthal',
        songName: "Now You Know" ,
        songUrl: "https://upload.wikimedia.org/wikipedia/commons/1/1e/Tom_Rosenthal_%28Musician%29.jpg",
        coverAlbum: "https://i.scdn.co/image/ab67616d0000b2734523edea415c3ddb92d3a34c",
        howl: null, 
        display: true

      },
      {
        id: 2,
        artist: 'Tom Rosenthal',
        songName: "Worries" ,
        songUrl: "https://upload.wikimedia.org/wikipedia/commons/1/1e/Tom_Rosenthal_%28Musician%29.jpg",
        coverAlbum: "https://i1.sndcdn.com/artworks-kWZFmkkpHKWw-0-t500x500.jpg",
        howl: null, 
        display: true

      },
      {  
        id: 3,
        artist: 'Patrick Watson',
        songName: "Je te laisserai des mots" ,
        songUrl: "https://upload.wikimedia.org/wikipedia/commons/1/1e/Tom_Rosenthal_%28Musician%29.jpg",
        coverAlbum: "https://i.scdn.co/image/ab67616d0000b27339372cb9fc75f395a5090a8d",
        howl: null, 
        display: true

      },    
      {  
        id: 4,
        artist: 'Patrick Watson',
        songName: "Lost With You" ,
        songUrl: "https://upload.wikimedia.org/wikipedia/commons/1/1e/Tom_Rosenthal_%28Musician%29.jpg",
        coverAlbum: "https://i1.sndcdn.com/artworks-kmUz33al9hrk-0-t500x500.jpg",
        howl: null, 
        display: true

      }, 
      {
        id: 5,
        artist: 'Edith Wiskers',
        songName: "Its Ok" ,
        songUrl: "https://upload.wikimedia.org/wikipedia/commons/1/1e/Tom_Rosenthal_%28Musician%29.jpg",
        coverAlbum: "https://cdns-images.dzcdn.net/images/cover/b78d0f72ee55ffaf69f625c2afee260e/200x200.jpg",
        howl: null, 
        display: true

      },
              {
        id: 6,
        artist: 'Edith Wiskers',
        songName: "Home" ,
        songUrl: "https://upload.wikimedia.org/wikipedia/commons/1/1e/Tom_Rosenthal_%28Musician%29.jpg",
        coverAlbum: "https://cdns-images.dzcdn.net/images/cover/98ee2fb23e1f5776a3b093ea25ee0255/500x500.jpg",
        howl: null, 
        display: true

      },
      {
        id: 7,
        artist: 'Coldplay',
        songName: "Trouble" ,
        songUrl: "https://upload.wikimedia.org/wikipedia/commons/1/1e/Tom_Rosenthal_%28Musician%29.jpg",
        coverAlbum: "https://upload.wikimedia.org/wikipedia/en/thumb/e/e2/Trouble_cover_art.jpg/220px-Trouble_cover_art.jpg",
        howl: null, 
        display: true

      },
              {
        id: 8,
        artist: 'Coldplay',
        songName: "Yellow" ,
        songUrl: "https://upload.wikimedia.org/wikipedia/commons/1/1e/Tom_Rosenthal_%28Musician%29.jpg",
        coverAlbum: "https://upload.wikimedia.org/wikipedia/en/9/9b/Yellow_cover_art.JPG",
        howl: null, 
        display: true

      },
      {
        id: 9,
        artist: 'Tom Odell',
        songName: "Heal" ,
        songUrl: "https://upload.wikimedia.org/wikipedia/commons/1/1e/Tom_Rosenthal_%28Musician%29.jpg",
        coverAlbum: "https://i1.sndcdn.com/artworks-000271046855-s5su2s-t500x500.jpg",
        howl: null, 
        display: true

      },
    ]    
    }),
  methods:{
    selectTrack (track) {
      this.selectedSong = track
    },
    playSong (index) {
      let selectedSongIndex = this.songs.findIndex(song => song === this.selectedSong)
      if (this.selectedSong) {
        if (this.selectedSong != this.currentTrack) {
          this.stopSong()
        }
        index = selectedSongIndex
      }else {
        index = this.index
      }
      let song = this.songs[index].howl      
      if (song.playing()) {
        return
      }else {
        song.play()
      }
      this.selectedTrack = this.songs[index]
      this.playing = true
      this.index = index
    }, 
    pauseSong () {
      this.currentTrack.howl.pause()
      this.playing = false
    },
    stopSong () {
      console.log(this.currentTrack)
      this.currentTrack.howl.stop()
      this.playing = false
    },
    loopSong (value) {
      this.loop = value
    },
    skip (direction) {
        let index = 0,
            lastIndex = this.songs.length - 1
        if (this.shuffle) {
          index = Math.round(Math.random() * lastIndex)
          while (index === this.index) {
            index = Math.round(Math.random() * lastIndex)
          }
        } else if (direction === "next") {
          index = this.index + 1
          if (index >= this.songs.length) {
            index = 0
          }
        } else {
          index = this.index - 1
          if (index < 0) {
            index = this.songs.length - 1
          }
        }
        this.skipTo(index)
    },
    skipTo (index) {
        if (this.currentTrack) {
          this.currentTrack.howl.stop()
        }
        this.playSong(index)
    },
    toggleShuffle (value) {
      this.shuffle = value
      console.log(this.shuffle)
    }
  },
  created: function () {
      this.songs.forEach( (track) => {
        let file = track.songName.replace(/\s/g, "_")
        track.howl = new Howl({
          src: [`./playlist/${file}.mp3`],
          onend: () => {
          if (!this.loop) {
            this.playSong(this.index)
          } else {
            this.skip('next')
          }
          }
        })
      })
    }, 
  computed:{
    currentTrack () {
      return this.songs[this.index]
    }
  } 
}
</script>
<style scoped src="@/assets/css/style.css"></style>
