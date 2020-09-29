<template>
<div>
    <v-row>
    <v-col cols="10">
        <v-text-field label="" solo v-model="textsearch" ></v-text-field>
    </v-col>
    <v-col cols="2">
        <v-btn @click="getitem()" large ><v-icon>mdi-magnify</v-icon></v-btn>
    </v-col>
    
    
    
</v-row>

<v-row>
     <v-col
                v-for="list in tmp"
                :key="list.trackId"
                class="d-flex child-flex"
                cols="4"
              >
            
        
              <nuxt-link :to="{ name: 'product-id',params: {id: list} }">
                  <v-hover
                  v-slot:default="{hover}">
                      
                      <v-card flat tile class="d-flex"
                      :elevation="hover ? 12 : 2"
                >
                
                     <v-img
                    :src="list.artworkUrl100"
                    aspect-ratio="1"
                    class="grey lighten-2 rounded"
                    
                    
                   
                  >
                    <p class="font-weight-bold grey" style="color:white"> {{list.trackName}}</p>
                    
                  </v-img> 

               
                  
                </v-card>

                  </v-hover>
                   

              </nuxt-link>
         
              
               
               
     </v-col>
          

            

     
    
</v-row>
    
</div>

    
    
</template>

<script>
import axios from "axios"

export default {
    data(){
        return{
            tmp : null,
            textsearch:"",
          

        }
    },
    methods:{
        getitem(){
            axios.get("https://itunes.apple.com/search?term=$"+this.textsearch+"&limit=30")
            .then(res => {
                this.tmp = res.data.results
                this.$emit("TMP",Object(res.data.results))
            })
            .catch(err => {
                console.error(err); 
            })

            
        }
    }
    
}
</script>

<style>

p{
  white-space: nowrap; 
  width: 100px; 
  overflow: hidden;
  text-overflow: clip; 
  
}


</style>