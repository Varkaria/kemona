<template>
  <div
    class="p-5 bg-gray-700 shadow-lg gap-4 xl:rounded-lg flex gap-4 items-center transform transition-all hover:(scale-95 opacity-60 cursor-pointer)"
    :style="`background: linear-gradient(rgb(31 41 55 / 80%), rgb(31 41 55)), url(https://api.varkaria.tech/kefull/banners/${creator.service}/${creator.id});`"
  >
    <img
      class="object-cover w-20 h-20 rounded-lg"
      :src="`https://api.varkaria.tech/kefull/icons/${creator.service}/${creator.id}`"
      :alt="creator.name"
      @error="$event.target.src = 'https://upload.wikimedia.org/wikipedia/commons/1/14/No_Image_Available.jpg'"
    >
    <div>
      <div class="flex gap-2">
        <a :class="`px-2 py-1 font-bold text-white rounded text-xs bg-${creator.service}`">{{ Capital(creator.service) }}</a>
      </div>
      <h1 class="mt-1 text-xl font-light text-light-200">
        {{ creator.name }}
      </h1>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    creator: {
      required: true,
      type: Object
    }
  },
  methods: {
    Capital (string) {
      return string.charAt(0).toUpperCase() + string.slice(1)
    }
  }
}
</script>
