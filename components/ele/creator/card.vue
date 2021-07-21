<template>
  <a
    class="p-5 bg-gray-700 shadow-lg gap-4 xl:rounded-lg flex gap-4 items-center transform transition-all hover:(scale-95 opacity-60 cursor-pointer)"
    :style="`background: linear-gradient(rgb(31 41 55 / 80%), rgb(31 41 55)), url(https://api.varkaria.tech/kefull/banners/${creator.service}/${creator.id});`"
    :href="`https://kemono.party/${creator.service}/user/${creator.id}`"
  >
    <img
      class="object-cover w-20 h-20 rounded-lg"
      :src="`https://api.varkaria.tech/kefull/icons/${creator.service}/${creator.id}`"
      :alt="creator.name"
      @error="$event.target.src = '/no-img.jpg'"
    >
    <div>
      <div class="flex gap-2">
        <a :class="`px-2 py-1 font-bold text-white rounded text-xs bg-${creator.service}`">{{ Capital(creator.service) }}</a>
      </div>
      <h1 class="w-40 text-xl font-light truncate overflow-ellipsis text-light-200">
        {{ creator.name }}
      </h1>
      <h1 class="w-40 mt-1 text-xs font-light text-light-200">
        Updated {{ creator.updated }}
      </h1>
      <div class="absolute top-0 flex flex-col justify-center h-full transform right-4">
        <div class="w-3 h-3 bg-gray-900 bg-opacity-50 rounded-full"></div>
        <div class="w-3 h-3 mt-2 bg-gray-900 bg-opacity-50 rounded-full"></div>
        <div class="w-3 h-3 mt-2 bg-gray-900 bg-opacity-50 rounded-full"></div>
      </div>
    </div>
  </a>
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
