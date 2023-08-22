<template>
  <header>
    <img :src="Logo" class="logo" alt="logo" />
    My Meme Generator in
    <img :src="LogoVue" class="" alt="vue" />
  </header>
</template>
<script setup>
import Logo from '../assets/logo.png';
import LogoVue from '../assets/vue.svg';
</script>
<style scoped></style>
