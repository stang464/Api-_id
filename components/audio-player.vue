

<template>
  <div>
    <v-card> 
        <v-btn @click="togglePlayback" icon ><v-icon x-large>mdi-play</v-icon></v-btn>
        <v-btn  @click="pause()" icon><v-icon>mdi-pause</v-icon></v-btn>
        
        <v-progress-linear :value="progress * 100" color="grey"></v-progress-linear>

    </v-card>
    
  </div>
</template>

<script>
  import VueHowler from 'vue-howler'

  export default {
    mixins: [VueHowler]
  }
</script>

<style >

</style>