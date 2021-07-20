<template>
  <div>
    <div class="header">
      <div
        class="relative px-4 py-12 mx-auto mt-4 overflow-hidden shadow-lg xl:rounded-xl md:max-w-full lg:max-w-screen-xl md:px-24 lg:px-8 lg:py-8"
        style="background: linear-gradient(rgb(31 41 55 / 80%), rgb(31 41 55)), url(https://konachan.com/sample c9eee6bf0ec092e27cc28e4e7b2814b7/Konachan.com%20-%20329361%20sample.jpg);"
      >
        <div class="flex grid items-center grid-cols-1 xl:grid-cols-2">
          <div class="px-6">
            <h2
              class="mx-auto font-sans text-5xl font-light leading-none tracking-tight text-left text-gray-200 md:mx-auto"
            >
              Artists
            </h2>

            <div class="pt-0 mt-4">
              <input
                v-model.trim="input"
                type="text"
                placeholder="Search users"
                class="relative w-full px-3 py-4 text-base text-gray-200 bg-gray-900 border-0 shadow outline-none xl:rounded bg-opacity-60 focus:outline-none focus:ring"
              >
            </div>
          </div>
          <div>
            <div class="p-5">
              <h2
                class="mx-auto mb-2 font-sans text-2xl font-light leading-none tracking-tight text-left text-gray-200 md:mx-auto"
              >
                Services
              </h2>
              <a v-for="(s, i) in services" :key="i" @click="filterData()">
                <EleServicesel
                  v-model="search.service"
                  :service="s"
                  :activeservice="search.service"
                />
              </a>
            </div>
            <div class="p-5">
              <h2
                class="mx-auto mb-2 font-sans text-2xl font-light leading-none tracking-tight text-left text-gray-200 md:mx-auto"
              >
                Sort by
              </h2>
              <a v-for="(s, i) in sort_by" :key="i" @click="filterData()">
                <EleSortsel
                  v-model="search.sort"
                  :sortby="s"
                  :activesortby="search.sort"
                />
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div v-if="load === false" class="mx-auto lg:max-w-screen-xl">
      <div
        :class="`creators grid grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 transition-all max-w-screen-xl mx-auto gap-4 mt-4 transition-all load-${search.load}`"
      >
        <EleCreatorCard v-for="(creator, i) in output" :key="i" :creator="creator" />
      </div>
    </div>
    <div v-else-if="load === true" class="flex justify-center mt-4">
      <div class="w-12 h-12 border-4 rounded-full border-white-600 loader" />
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      load: false,
      result: [],
      output: [],
      services: [
        'All',
        'Patreon',
        'Pixiv Fanbox',
        'Gumroad',
        'SubscribeStar',
        'Discord',
        'DLsite',
        'Fantia'
      ],
      sort_by: ['Date Indexed', 'Alphabetical Order', 'Service'],
      search: {
        service: 'all',
        load: false,
        order: 'desc',
        sort: 'indexed',
        query: ''
      },
      pag: {
        limit: 25,
        skip: 0
      }
    }
  },
  computed: {
    input: {
      get () {
        return this.search.query
      },
      set (val) {
        if (this.search.timeout) {
          clearTimeout(this.search.timeout)
        }
        this.search.timeout = setTimeout(() => {
          this.search.query = val
          this.filterData()
        }, 300)
      }
    }
  },
  created () {
    this.FetchData()
  },
  methods: {
    sleep (ms) {
      return new Promise(resolve => setTimeout(resolve, ms))
    },
    async FetchData () {
      this.load = true
      const res = await this.$axios.$get('https://api.varkaria.tech/kemono/creators')
      this.result = res
      this.filterData()
      this.load = false
    },
    async filterData (s = null) {
      this.search.load = true

      let filteredCreators = this.result
      let ser = ''

      if (this.search.order === 'desc') {
        filteredCreators.reverse()
      }

      if (this.search.service !== 'all') {
        ser = this.search.service
      }

      filteredCreators = await filteredCreators
        .filter(creator => creator.service === (ser || creator.service))
        .sort((a, b) => {
          if (this.search.order === 'desc') {
            return this.search.sort === 'indexed'
              ? Date.parse(a.indexed) - Date.parse(b.indexed)
              : a[this.search.sort].localeCompare(b[this.search.sort])
          } else {
            return this.search.sortBy === 'indexed'
              ? Date.parse(b.indexed) - Date.parse(a.indexed)
              : b[this.search.sort].localeCompare(a[this.search.sort])
          }
        })
        .filter((creator) => {
          return creator.name.match(
            new RegExp(
              this.search.query.replace(
                // eslint-disable-next-line no-useless-escape
                /[-\/\\^$*+?.()|[\]{}]/g,
                '\\$&'
              ),
              'i'
            )
          )
        })

      this.output = filteredCreators.slice(0, 20)

      await this.sleep(1000)
      this.search.load = false
      return 'ok'
    }
  }
}
</script>

<style>
.load-true {
  opacity: 0.5;
}

@keyframes loader-rotate {
  0% {
    transform: rotate(0);
  }

  100% {
    transform: rotate(360deg);
  }
}

.loader {
  border-right-color: transparent;
  animation: loader-rotate 1s linear infinite;
}
</style>
