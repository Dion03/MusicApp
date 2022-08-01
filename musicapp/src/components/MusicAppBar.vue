<template>
  <v-container class="pa-0 white-text" fluid style="padding: 0 !important; ">
        <v-row no-gutters height="100%" >
      <v-app-bar style="background: linear-gradient(163deg, rgba(72,7,6,1) 0%, rgba(0,0,0,1) 100%);">
        <v-btn icon class="ml-16 menuIcons">
          <v-icon>mdi-home</v-icon>
          Home
        </v-btn>
        <v-btn icon class="ml-16 menuIcons">
          <v-icon>mdi-magnify</v-icon>
          Search
        </v-btn>
        <v-btn icon class="ml-16 menuIcons">
          <v-icon>mdi-music</v-icon>
          Library
        </v-btn>
        <v-btn icon class="ml-16 menuIcons">
          <v-icon>mdi-account</v-icon>
          Account
        </v-btn>
      </v-app-bar>
    </v-row>
    <v-row no-gutters height="100%" >
      <v-row class="topRow artistBar" no-gutters style="background: linear-gradient(163deg, rgba(72,7,6,1) 0%, rgba(0,0,0,1) 100%);;">
        <v-card v-for="artist in arists" :key="artist.id" elevation="4" class="artistCards ml-auto mr-16 mt-8 cardZoom">
          <v-img class="artistImg" :src="artist.img"></v-img>
            <v-overlay absolute color="#F32626">
              <v-card flat color="transparent">
                <v-card-title class="text-left">{{artist.name}}</v-card-title>
              </v-card>
            </v-overlay>
        </v-card> 
      </v-row>
    </v-row>
  </v-container>
</template>

<script>
export default {
data: () => ({
      picture: '',
      arists: [
        {
          id: 1,
          name: 'Tom Rosenthal',
          img: "https://upload.wikimedia.org/wikipedia/commons/1/1e/Tom_Rosenthal_%28Musician%29.jpg",
        },
        {  
          id: 2,
          name: 'Patrick Watson',
          img: "https://cdns-images.dzcdn.net/images/artist/a08e1fed4187bf02898b1591f2731695/500x500.jpg",
        },    
        {
          id: 3,
          name: 'Edith Wiskers',
          img: "https://angartwork.akamaized.net/webp/?id=1146645539&size=296",
        },
        {
          id: 4,
          name: 'Coldplay',
          img: "https://upload.wikimedia.org/wikipedia/commons/2/2e/ColdplayBBC071221_%28cropped%29.jpg",
        },
        {
          id: 5,
          name: 'Tom Odell',
          img: 'https://i.scdn.co/image/ab67616d00001e029adb17697c5a5bb02b5cebb7',
        },
        // {
        // id: 6,
        // name: "Sufjan Stevens",
        // img: "https://upload.wikimedia.org/wikipedia/commons/3/33/Sufjan_Stevens_performing_at_Pitchfork%2C_2016.jpg"
        // }
      ]
    }),
}
</script>
<style scoped>
.menuIcons{
  color: #d4d4d4 !important;
}
.artistCards{
  background-color:#741214 !important;
  height: 200px;
  width: 200px;
  border-radius: 1em;
}
.artistBar{
  height: 275px;
}
.artistImg{
width: 200px;
height:200px;
border-radius: 1em;
}
.cardZoom:hover{
      transform: scale(1.2);

}
</style>