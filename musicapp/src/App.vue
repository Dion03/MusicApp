<template>
  <v-app>
    <v-main>
      <MusicApp/>
    </v-main>
  </v-app>
</template>

<script>
  import MusicApp from '@/components/MusicApp'


export default {
  name: 'App',
    components: {
      MusicApp,
    },
  data: () => ({
    //
  }),
};
</script>
