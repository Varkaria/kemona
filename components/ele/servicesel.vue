<template>
  <button
    class="px-2 py-1 m-1 font-semibold bg-gray-500 rounded-md outline-none text-light-100 focus:outline-none"
    :class="getClass()"
    @click="updateService()"
  >
    {{ service }}
  </button>
</template>

<script>
export default {
  // eslint-disable-next-line vue/require-prop-types
  props: ['service', 'activeservice', 'input'],
  methods: {
    updateService () {
      this.$emit('input', this.toclass(this.service))
    },
    toclass (w) {
      if (w === 'Pixiv Fanbox') { return 'fanbox' }
      return w.toLowerCase().replace(' ', '_')
    },
    getClass () {
      if (this.activeservice === this.toclass(this.service)) {
        if (this.toclass(this.service) === 'all') {
          return '!bg-green-700'
        }
        console.log('found selection')
        return `!bg-${this.toclass(this.service)}`
      }
    }
  }
}
</script>

<style>
.probid {
  pointer-events: none;
}
</style>
