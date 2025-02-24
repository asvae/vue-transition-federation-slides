<script setup>
import Reveal from 'reveal.js';
import Markdown from 'reveal.js/plugin/markdown/markdown.esm.js';
import { onMounted } from 'vue'
import AnotherSection from './AnotherSection.vue'

onMounted(() => {
  Reveal.initialize({
    plugins: [Markdown]
  });
})
</script>

<template>
  <div class="reveal">
    <div class="slides">
      <section>Single Horizontal Slide</section>
      <section>
        <section>Vertical Slide 1</section>
        <section>Vertical Slide 2</section>
      </section>
      <AnotherSection/>
    </div>
  </div>
</template>

<style>
@import url('../node_modules/reveal.js/dist/reveal.css');
@import url('../node_modules/reveal.js/dist/theme/black.css');

#app {
  width: 100%;
  height: 100%;
}
</style>
