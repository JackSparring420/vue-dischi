<template>
  <main>
    <div id="filtro">
      <FilterMusicGenre @search="searching" />
    </div>
    <div id="albums-container">
      <Album v-for="album, i in filteredListaAlbum" :key="i" :details="album" />
    </div>
  </main>
</template>

<script>
import axios from "axios";
import Album from "@/components/Album.vue";
import FilterMusicGenre from "@/components/FilterMusicGenre.vue";

export default {
  name: "Albums",
  components: {
    Album,
    FilterMusicGenre,
  },
  data() {
    return {
      apriUrl: "https://flynn.boolean.careers/exercises/api/array/music",
      albums: [],
      searchText: "",
    };
  },
  created() {
    this.getCharachters();
  },
  methods: {
    getCharachters() {
      console.log("ho finito la prima parte");

      axios.get(this.apriUrl).then((result) => {
        this.albums = result.data.response;
        console.log(result.data.response);
      });
    },
    searching(genere) {
      this.searchText = genere;
      console.log(this.searchText);
    },


  },

  computed: {
    filteredListaAlbum() {
      if (this.searchText === "All") {
        return this.albums;
      }

      return this.albums.filter((item) => {
        return item.genre.toLowerCase().includes(this.searchText.toLowerCase());
      });
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
main {
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
  #filtro{
    display: flex;
    justify-content: center;
    padding-top: 50px ;
  }
</style>
