<template>
  <header>
    <b-navbar class="nav-color-background">
      <b-collapse is-nav class="d-flex justify-content-around">
        <b-navbar-brand href="#">
          <img src="@/assets/images/logo-nav-bar.webp" />
        </b-navbar-brand>

        <b-navbar-nav class="nav-config">
          <b-nav-item href="#">PatchLog</b-nav-item>
          <b-nav-item href="#">Informações</b-nav-item>
          <b-nav-item href="#">DropList</b-nav-item>
        </b-navbar-nav>

        <b-navbar-nav class="nav-config border-config">
          <b-nav-item href="#">DOWNLOAD</b-nav-item>
          <b-nav-item href="#">CRIAR CONTA</b-nav-item>
        </b-navbar-nav>
      </b-collapse>
    </b-navbar>
  </header>
</template>

<script>
export default {
  name: "Header",
};
</script>

<style src="./style.scss" lang="scss" scoped />
