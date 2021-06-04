<template>
  <div
    class="movielist"
    v-for="(item, index) in movieDetails"
    v-bind:key="index"
  >
    <img class="poster" v-bind:src="item.Poster" alt="" />
    <div class="right">
      <div class="title">{{ item.Title }}</div>
      <div class="year">{{ item.Year }}</div>
    </div>
  </div>
</template>
<script>
export default {
  name: "movieList",
  props: {
    movieDetails: Array,
  },
};
</script>

<style>
.movielist {
  display: flex;
  align-items: center;
  justify-content: flex-start;
  height: 100px;
  background-color: white;
  border-bottom: 1px solid black;
}

.right{
    display: flex;
    justify-content: flex-start;
    margin-left: 10px;
}

.poster {
  height: 80px;
}

.title{
    font-weight: 700;
}

.year{
    font-style: italic;
    margin-left: 10px;
}
</style>