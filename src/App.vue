<template>
  <div class="container">
    <nav>
      <div class="title">
        <h1 class="logoLetter">S</h1>
        <h1>Sample Blog</h1>
      </div>
      <div class="nav">
        <router-link to="/">Home</router-link> |
        <router-link to="/about">About</router-link>
      </div>
    </nav>

    <router-view />
  </div>
</template>

<style>
@font-face {
  font-family: "Montserrat-Regular";
  src: url("./assets/fonts/Montserrat-Regular.ttf");
}

* {
  margin: 0;
  padding: 0;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
}

#app {
  font-family: "Montserrat-Regular";
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  background-color: #f3f5f8;
  border-radius: 40px;
  min-height: 98.382vh;
}

nav {
  display: flex;
  background-color: #fff;
  justify-content: space-between;
  align-items: center;
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
  text-decoration: none;
}

nav a.router-link-exact-active {
  color: #fa7c65;
}
.title {
  display: flex;
  align-items: center;
}

.title .logoLetter {
  margin-right: 20px;
  background-color: #fa7c65;
  color: #fff;
  padding: 10px 15px;
  border-radius: 10px;
}
</style>
