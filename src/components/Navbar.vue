<template>
  <header class="background shadow-lg h-16 flex justify-between items-stretch">
    <router-link
      :to="{ name: 'home' }"
      class="font inline-flex drop-shadow-lg items-center h-full px-5 font-black text-sm"
    >
      <img src="/recipefier.svg" width="20" height="20" /> Recipefier
    </router-link>
    <div class="flex items-center gap-1">
      <router-link
        :to="{ name: 'byName' }"
        class="inline-flex font items-center text-xs px-1 drop-shadow-lg h-full transition-colors hover:bg-gray-500 hover:text-white"
      >
        Search Recipes
      </router-link>
      <router-link
        :to="{ name: 'byLetter' }"
        class="inline-flex font items-center text-xs px-1 drop-shadow-lg h-full transition-colors hover:bg-gray-500 hover:text-white"
      >
        Recipes By Letter
      </router-link>
      <router-link
        :to="{ name: 'ingredients' }"
        class="inline-flex font items-center text-xs px-1 drop-shadow-lg h-full transition-colors hover:bg-gray-500 hover:text-white"
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
