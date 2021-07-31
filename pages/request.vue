<template>
  <div>
    <div class="header">
      <div
        class="relative px-4 py-8 mx-auto mt-4 overflow-hidden shadow-lg xl:rounded-xl md:max-w-full lg:max-w-screen-xl md:px-24 lg:px-8 lg:py-8"
        style="background: linear-gradient(rgb(31 41 55 / 80%), rgb(31 41 55)), url(/headers/request.jpg);"
      >
        <div
          class="flex grid items-center grid-cols-1 transition-all xl:grid-cols-2"
          v-bind:class="{ 'opacity-50 pointer-events-none': load }"
        >
          <div class="px-6">
            <h2
              class="mx-auto font-sans text-5xl font-light leading-none tracking-tight text-left text-gray-200 md:mx-auto"
            >
              Request
            </h2>
            <div class="pt-0 mt-4">
              <input
                v-model.trim="input"
                type="text"
                placeholder="Title"
                class="relative w-full px-3 py-4 text-base text-gray-200 bg-gray-900 border-0 shadow outline-none xl:rounded bg-opacity-60 focus:outline-none focus:ring"
              />
            </div>
          </div>
          <div>
            <div class="p-5 -mb-4">
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
            <div class="p-5 -mb-4">
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
            <div class="grid grid-cols-2 gap-2 p-5 -mb-4">
              <div>
              <h2 
                class="mx-auto mb-2 font-sans text-2xl font-light leading-none tracking-tight text-left text-gray-200 md:mx-auto"
              >
                Status
              </h2>
              <a v-for="(s, i) in status" :key="i" @click="filterData()">
                <EleSortsel
                  v-model="search.sort"
                  :sortby="s"
                  :activesortby="search.sort"
                />
              </a>
            </div>
            <div class="-ml-8">
              <h2 
                class="mx-auto mb-2 font-sans text-2xl font-light leading-none tracking-tight text-left text-gray-200 md:mx-auto"
              >
                Max Price
              </h2>
              <input
                v-model.trim="input"
                type="text"
                placeholder="Amount"
                class="relative w-3/4 px-3 py-2 text-base text-gray-200 bg-gray-900 border-0 shadow outline-none xl:rounded bg-opacity-60 focus:outline-none focus:ring"
              />
            </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
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
      sort_by: ['Votes', 'Date posted', 'Price'],
      status: ['Open', 'Fulfilled', 'Closed'],
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
  }
}
</script>
