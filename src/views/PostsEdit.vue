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
    editPosts() {
      axios
        .patch(`/posts/${this.$route.params.id}`, this.post)
        .then((response) => {
          console.log(response.data);
          this.post = response.data;
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
    <h1>Edit Post</h1>
    <form v-on:submit.prevent="editPosts()">
      <ul>
        <li v-for="error in errors" v-bind:key="error">{{ error }}</li>
      </ul>
      <p>
        Title:
        <input type="text" v-model="post.title" />
      </p>
      <p>
        Body:
        <input type="text" v-model="post.body" />
      </p>
      <p>
        Image:
        <input type="text" v-model="post.image" />
      </p>
      <input type="submit" value="Edit" />
    </form>
  </div>
</template>

<style></style>
