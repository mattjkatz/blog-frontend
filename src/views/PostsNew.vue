<script>
import axios from "axios";

export default {
  data: function () {
    return {
      message: "Create a new blog post!",
      posts: [],
      newPosts: {},
      errors: [],
    };
  },
  created: function () {},
  methods: {
    createPosts() {
      axios
        .post("/posts", this.newPosts)
        .then((response) => {
          console.log(response);
          this.$router.push("/posts");
        })
        .catch((error) => {
          this.errors = error.response.data.errors;
          console.log(this.errors);
        });
    },
  },
};
</script>

<template>
  <div class="home">
    <h1 id="page-title">{{ message }}</h1>
    <div v-for="error in errors" v-bind:key="error">
      <p id="error">{{ error }}</p>
    </div>
    <form v-on:submit.prevent="createPosts()">
      <p>
        Post Title:
        <input type="text" v-model="newPosts.title" />
      </p>
      <p>
        Post Body:
        <input type="text" v-model="newPosts.body" />
      </p>
      <p>
        <small v-if="newPosts?.body?.length > 0 && newPosts?.body?.length <= 240">
          You have {{ 240 - newPosts.body.length }} characters left
        </small>
        <small v-if="newPosts?.body?.length > 240" class="text-danger">*Post body has exceeded the max limit</small>
      </p>
      <p>
        Post Image:
        <input type="text" v-model="newPosts.image" />
      </p>
      <input type="submit" value="Post" />
    </form>
  </div>
</template>

<style></style>
