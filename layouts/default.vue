<template>
  <div class="flex relative">
    <!-- Contenu principal de la page -->
    <div
      :class="
        drawerOpen
          ? 'flex-auto  mr-64 '
          : 'flex-auto transition-margin duration-500 ease-linear'
      "
      class="min-h-screen transition-all duration-500 ease-in-out"
    >
      <button
        @click="toggleDrawer"
        class="z-50 absolute top-5 left-5 m-4 py-1 px-4 bg-gray-100 text-gray-700 font-medium rounded-full hover:bg-gray-200"
      >
        Index
      </button>
      <slot />
    </div>
    <!-- Drawer fixe qui se déplace pas son contenu -->
    <div
      :class="drawerOpen ? 'w-1/3' : 'w-0'"
      class="fixed inset-y-0 right-0 transition-width duration-500 ease-in-out overflow-hidden"
    >
      <div
        class="p-4 w-full h-full fixed rounded-l-3xl bg-gray-100 text-gray-600"
        @click="drawerOpen = !drawerOpen"
      >
        <p class="text-2xl pb-6">Index</p>
        <ul
          v-for="index in indexes"
          :key="index.id"
          class="flex flex-col cursor-pointer p-2 hover:bg-gray-200 rounded-l-3xl"
        >
          <li>
            <NuxtLink :to="`/${index.page}`">{{ index.name }}</NuxtLink>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script setup>
const drawerOpen = ref(false)

const indexes = [
  { id: 'chart1', name: 'Users cumul', page: 'userscumul' },
  { id: 'chart2', name: 'users trend 30 last days', page: 'userstrend' },
  { id: 'chart3', name: 'home', page: '' },
]

function toggleDrawer() {
  drawerOpen.value = !drawerOpen.value
}
</script>

<style>
.transition-width {
  transition: width 0.5s ease-in-out;
}

.transition-margin {
  transition: margin-right 0.5s ease-linear;
}

body {
  overflow-x: hidden;
}
</style>
