<script>
import axios from "axios";

export default {
  data: function () {
    return {
      message: "Woah, look at this cool post",
      post: {},
    };
  },
  created: function () {
    this.showPosts();
  },
  methods: {
    showPosts() {
      axios.get(`/posts/${this.$route.params.id}`).then((response) => {
        console.log(response.data);
        this.post = response.data;
      });
    },
  },
};
</script>

<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <h3>{{ post.title }}</h3>
    <p>{{ post.body }}</p>
    <img v-bind:src="post.image" v-bind:alt="post.title" />
    <div>
      <router-link to="/posts">Back to all posts</router-link>
      <router-link v-bind:to="`/posts/${post.id}/edit`">Edit post</router-link>
    </div>
  </div>
</template>

<style></style>
