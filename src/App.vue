<template>
  <nav>
    <router-link to="/">Home</router-link>
    |
    <router-link to="/about">About</router-link>
    |
    <router-link to="/Sample">Sample</router-link>
    |
    <router-link to="/signup">Signup</router-link>
    |
    <router-link to="/login">Login</router-link>
    |
    <router-link to="/logout">Logout</router-link>
    |
    <router-link to="/posts">Posts</router-link>
    |
    <router-link to="/posts/new">NewPost</router-link>
  </nav>
  <router-view />
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}

#page-title {
  margin: auto;
  border: 1px solid grey;
}

#paragraphs {
  margin: auto;
  max-width: 66%;
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

#error {
  color: red;
}
</style>
