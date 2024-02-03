<template>
  <header class="background shadow-lg h-16 flex justify-between items-stretch">
    <router-link
      :to="{ name: 'home' }"
      class="font inline-flex drop-shadow-lg items-center h-full px-5 font-black text-3xl"
    >
      <img src="/recipefier.svg" width="50" height="50" /> Recipefier
    </router-link>
    <div class="flex items-center gap-1">
      <router-link
        :to="{ name: 'byName' }"
        class="inline-flex items-center px-2 drop-shadow-lg h-full transition-colors font-black hover:bg-gray-500 hover:text-white"
      >
        Search Recipes
      </router-link>
      <router-link
        :to="{ name: 'byLetter' }"
        class="inline-flex items-center px-2 drop-shadow-lg h-full transition-colors font-black hover:bg-gray-500 hover:text-white"
      >
        Recipes By Letter
      </router-link>
      <router-link
        :to="{ name: 'ingredients' }"
        class="inline-flex items-center px-2 drop-shadow-lg h-full transition-colors font-black hover:bg-gray-500 hover:text-white"
      >
        Recipes By Ingredients
      </router-link>
    </div>
  </header>
</template>
<style>
.background {
  background: #e3e2e2;
}
.font {
  color: #282828;
}
</style>
