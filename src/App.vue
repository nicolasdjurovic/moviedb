<template>
  <div class="container">
    <div class="inputcontainer">
      <input type="text" placeholder="Search a movie or show..." v-model="searchTerm"/>
      <select v-model="searchType">
        <option value="movie" selected>Movies</option>
        <option value="series">Series</option>
        <option value="episode">Episodes</option>
      </select>
      <button @click="searchDB">Search</button>
    </div>
    <div class="movielistcontainer">
      <movieList v-bind:movieDetails="this.searchResults" />
    </div>
  </div>
</template>

<script>
import movieList from "./components/movieList";
import axios from "axios";

export default {
  name: "App",
  data() {
    return {
      searchTerm: "",
      searchType: "",
      searchResults: {},
    };
  },
  components: {
    movieList,
  },
  methods: {
    searchDB() {
      axios
        .get("http://www.omdbapi.com/", {
          params: {
            apikey: "2b2c454e",
            s: this.searchTerm,
            type: this.searchType,
          },
        })
        .then((response) => {
          this.searchResults = response.data.Search;
        });
    },
  },
};
</script>

<style lang="scss">

*{
  padding: 0;
  border: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.container {
  width: 100%;
  height: 400px;
}

.inputcontainer {
  height: 50px;
  width: 100%;
  display: flex;
  justify-content: space-between;
  align-items: center;

  input {
    width: 100%;
    height: 50px;
    background-color: #2c3e50;
    color: white;
    padding-left: 20px;
  }

  input::placeholder{
    color: white;
    padding: 20px;
  }

  button {
    height: 50px;
    width: 100px;
    cursor: pointer;
    background-color: rgb(255, 208, 0);
  }

  select{
    height: 50px;
    width: 100px;
        background-color: rgb(255, 208, 0);
  }

  select:focus, input:focus{
    outline: none;
  }


}
</style>