<script setup>
import { ref } from 'vue';

const meme = ref({
  topText: 'hello',
  bottomText: 'world',
  url: 'http://i.imgflip.com/1bij.jpg'
});

function getMemeImage() {
  fetch('https://api.imgflip.com/get_memes')
    .then((res) => res.json())
    .then((data) => {
      const allMemes = data.data.memes;
      const randomNumber = Math.floor(Math.random() * allMemes.length);
      meme.value.url = allMemes[randomNumber].url;
    });
}
</script>
<template>
  <main>
    <div class="form">
      <input
        class="input"
        type="text"
        name="topText"
        placeholder="First text"
        v-model="meme.topText"
        v-on:click="meme.topText = ''"
      />
      <input
        class="input"
        type="text"
        name="bottomText"
        placeholder="Second text"
        v-model="meme.bottomText"
        v-on:click="meme.bottomText = ''"
      />
      <button type="submit" @click="getMemeImage">Get a new meme image</button>
    </div>
    <div class="output">
      <span class="text-top">{{ meme.topText }}</span>
      <span class="text-bottom">{{ meme.bottomText }}</span>
      <img :src="meme.url" />
    </div>
  </main>
</template>
