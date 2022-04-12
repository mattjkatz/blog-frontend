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
  <div class="home">
    <h1 id="page-title">{{ message }}</h1>
    <div v-for="post in posts" v-bind:key="post.id">
      <div>
        <h2 id="post-title">{{ post.title }}</h2>
        <p id="paragraph">{{ post.body }}</p>
        <router-link v-bind:to="`/posts/${post.id}`">
          <img v-bind:src="post.image" v-bind:alt="post.title" style="max-width: 250px" />
        </router-link>
        <!-- <div></div> -->
        <hr />
      </div>
    </div>
  </div>
</template>

<style>
.column {
  float: left;
  width: 50%;
  padding: 10px;
}

#paragraph {
  margin: auto;
  max-width: 30%;
  min-width: 600px;
  padding-left: 200px;
  padding-right: 200px;
}

#post-title {
  color: grey;
  font-size: 150%;
  font-weight: lighter;
  padding: 0px 0px 12px 0px;
  border-bottom: 1px solid grey;
  text-transform: uppercase;
}
</style>
