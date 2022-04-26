<template>
  <div id="global-container">
    <div id="container">
      <Header />
      <!-- <header class="header">
        <div id="nav">
          <router-link to="/">Home</router-link> |
          <router-link to="/hobby">hobby</router-link> |
          <router-link to="/children">contact</router-link> |
        </div>
      </header> -->
      <router-view />
    </div>
  </div>
</template>

<style>
#app {
  font-family: "Beau Rivage", cursive, Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
#global-container {
  position: relative;
}

#container {
  position: relative;
  margin: 0 auto;
}

.header {
  z-index: 100;
  position: fixed;
  display: flex;
  width: 100%;
  height: 60px;
  z-index: 10;
  align-items: center;
  justify-content: center;
  background: rgba(255, 255, 255, 0.5);
}

svg {
  position: fixed;
  fill: pink;
  top: 0;
  left: 0;
}

#nav {
  padding: 30px;
  text-align: center;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
<script>
import Header from "@/components/Header";

export default {
  name: "App",

  components: {
    Header,
  },
};
</script>
