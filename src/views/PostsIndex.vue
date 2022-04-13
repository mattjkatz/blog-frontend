<script>
import axios from "axios";

export default {
  data: function () {
    return {
      message: "Welcome to me bLoG",
      posts: [],
      currentPost: {},
      hover: false,
    };
  },
  created: function () {
    this.postsIndex();
  },
  methods: {
    postsIndex() {
      axios.get("/posts").then((response) => {
        console.log(response.data);
        this.posts = response.data;
      });
    },
  },
};
</script>

<template>
  <div class="home container row">
    <h1 id="page-title">{{ message }}</h1>
    <div
      v-for="post in posts"
      v-bind:key="post.id"
      v-bind:class="{ selected: post === currentPost }"
      v-on:mouseover="currentPost = post"
      class="col"
    >
      <div class="card" style="width: 18rem">
        <img v-bind:src="post.image" class="card-img-top" alt="..." />
        <div class="card-body">
          <p class="card-text">
            Some quick example text to build on the card title and make up the bulk of the card's content.
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<style>
.selected .card-body {
  color: white;
  background-color: rgb(160, 160, 160);
}
</style>
