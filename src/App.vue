<template>
  <nav class="navbar navbar-expand-lg navbar-light bg-light">
    <div class="container-fluid">
      <a class="navbar-brand" href="#">Bl0g</a>
      <button
        class="navbar-toggler"
        type="button"
        data-bs-toggle="collapse"
        data-bs-target="#navbarScroll"
        aria-controls="navbarScroll"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarScroll">
        <ul class="navbar-nav me-auto my-2 my-lg-0 navbar-nav-scroll" style="--bs-scroll-height: 100px">
          <li class="nav-item">
            <a class="nav-link active" aria-current="page" href="/">Home</a>
          </li>
          <li class="nav-item">
            <a class="nav-link active" aria-current="page" href="/posts">Posts</a>
          </li>
          <li class="nav-item">
            <a class="nav-link active" aria-current="page" href="/posts/new">New</a>
          </li>
          <li v-if="!isLoggedIn" class="nav-item">
            <a class="nav-link active" aria-current="page" href="/signup">Signup</a>
          </li>
          <li v-if="!isLoggedIn" class="nav-item">
            <a class="nav-link active" aria-current="page" href="/login">Login</a>
          </li>
          <li v-if="isLoggedIn" class="nav-item">
            <a class="nav-link active" aria-current="page" href="/logout">Logout</a>
          </li>
        </ul>
        <form class="d-flex">
          <input class="form-control me-2" type="search" placeholder="Search" aria-label="Search" />
          <button class="btn btn-outline-success" type="submit">Search</button>
        </form>
      </div>
    </div>
  </nav>
  <router-view />
</template>

<script>
export default {
  data: function () {
    return {
      isLoggedIn: false,
    };
  },
  watch: {
    $route: function () {
      this.isLoggedIn = !!localStorage.jwt;
    },
  },
};
</script>

<style>
body {
  text-align: center;
}

#page-title {
  padding: 30px;
  font-weight: bolder;
  font-size: 5rem;
  border: 1px solid grey;
}

#error {
  color: red;
}
</style>
