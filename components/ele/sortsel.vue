<template>
  <button
    class="px-2 py-1 m-1 font-semibold bg-gray-500 rounded-md outline-none text-light-100 focus:outline-none"
    :class="getClass()"
    @click="updatesortby()"
  >
    {{ sortby }}
  </button>
</template>

<script>
export default {
  // eslint-disable-next-line vue/require-prop-types
  props: ['sortby', 'activesortby', 'input'],
  methods: {
    updatesortby () {
      this.$emit('input', this.toclass(this.sortby))
    },
    toclass (w) {
      if (w === 'Date Indexed') { return 'indexed' }
      if (w === 'Alphabetical Order') { return 'name' }
      if (w === 'Service') { return 'service' }
    },
    getClass () {
      if (this.activesortby === this.toclass(this.sortby)) {
        return 'bg-green-700 probid'
      }
    }
  }
}
</script>
