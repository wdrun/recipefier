<template>
  <a
    :href="href"
    target="_blank"
    class="youtube rounded hover:bg-red-600 border-red-600 transition-colors"
  >
    <slot>Watch it on YouTube</slot>
  </a>
</template>

<style>
.youtube {
  margin: 4px;
  padding-left: 3%;
  padding-right: 3%;
  padding-top: 2%;
  padding-bottom: 2%;
  border-radius: 20%;
  border: 2%;
  color: white;
  border-color: rgb(250, 0, 0);
  background: rgb(250, 0, 0);
}
:hover .youtube {
  background: rgb(250, 0, 10);
  border-color: rgb(250, 0, 10);
}
</style>

<script setup>
const props = defineProps({
  href: String,
});
</script>
