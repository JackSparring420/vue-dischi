<template>
  <main>
    <div id="albums-container">
        <Album v-for="album, i in albums" :key="i" :details="album"/>
    </div>
  </main>
</template>

<script>
import axios from "axios"
import Album from "@/components/Album.vue"
export default {
  name: 'Albums',
    components: {
    Album
  },
 data() {
     return {
         apriUrl: 'https://flynn.boolean.careers/exercises/api/array/music',
         albums: []
     }
 },
 created () {
     this.getCharachters()
     },
    methods: {
        getCharachters(){
            console.log("ho finito la prima parte");
            
            axios
            .get(this.apriUrl)
            .then((result) => {
                this.albums = result.data.response
                console.log(result.data.response);
            })

        }
    },

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

  main{
    background-color: #1e2d3b;
  }
    #albums-container {
        width: 60%;
        margin: auto;
        display: flex;
        flex-wrap: wrap;
        gap: 10px;
        padding: 50px;
        
        .album {
          flex-wrap: wrap;
          justify-content: space-between;
            margin-top: 20px;
        }
    }


</style>
