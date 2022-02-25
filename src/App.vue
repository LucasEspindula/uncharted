<template>
  <div id="app">
    <Header />
    <template>
      <Home />
    </template>
    <Footer />
  </div>
</template>

<script>
import Header from "./components/Header/Header.vue";
import Home from "./pages/Home/Home.vue";
import Footer from "./components/Footer/Footer.vue";

export default {
  name: "App",
  components: {
    Header,
    Home,
    Footer,
  },
};
</script>

<style></style>
