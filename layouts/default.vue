<template>
  <div>
    <Navbar />
    <transition name="trans" mode="out-in">
      <Nuxt />
    </transition>
    <footer class="flex justify-center w-full my-20 text-light-300">
      <ul class="flex gap-4">
        <li>
          <a target="_blank" class="font-medium">Frontend</a>
        </li>
        <li>
          <a target="_blank" class="font-medium">Source code</a>
        </li>
        <li>
          <a target="_blank" class="font-medium">Backend</a>
        </li>
      </ul>
    </footer>
  </div>
</template>

<script>
export default {
  head: {
    bodyAttrs: {
      class:
        "flex flex-col h-screen bg-gray-900 scrollbar-thin scrollbar-thumb-gray-700 scrollbar-track-gray-300 h-32 overflow-y-scroll",
    },
  },
};
</script>
