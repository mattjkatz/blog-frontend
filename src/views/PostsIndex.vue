<script>
import axios from "axios";

export default {
  data: function () {
    return {
      message: "Welcome to me bLoG",
      posts: [],
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
  <div class="card" style="width: 18rem">
    <img src="https://c.tenor.com/-p-p8MvwM3AAAAAM/dog-funny.gif" class="card-img-top" alt="..." />
    <div class="card-body">
      <p class="card-text">
        Some quick example text to build on the card title and make up the bulk of the card's content.
      </p>
    </div>
  </div>
  <div class="home">
    <h1 id="page-title">{{ message }}</h1>
    <div v-for="post in posts" v-bind:key="post.id">
      <div class="card" style="width: 18rem">
        <img src="https://c.tenor.com/-p-p8MvwM3AAAAAM/dog-funny.gif" class="card-img-top" alt="..." />
        <div class="card-body">
          <p class="card-text">
            Some quick example text to build on the card title and make up the bulk of the card's content.
          </p>
        </div>
      </div>
      <!-- <div>
        <h2 id="post-title">{{ post.title }}</h2>
        <p id="paragraph">{{ post.body }}</p>
        <router-link v-bind:to="`/posts/${post.id}`">
          <img v-bind:src="post.image" v-bind:alt="post.title" style="max-width: 250px" />
        </router-link>
        <hr />
      </div> -->
    </div>
  </div>
</template>

<style></style>
