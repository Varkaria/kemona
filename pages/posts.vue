<template>
  <div>
    <div class="header">
      <div
        class="relative px-4 py-12 mx-auto mt-4 overflow-hidden shadow-lg xl:rounded-xl md:max-w-full lg:max-w-screen-xl md:px-24 lg:px-8 lg:py-8"
        style="background: linear-gradient(rgb(31 41 55 / 80%), rgb(31 41 55)), url(/headers/request.jpg);"
      >
        <div
          class="flex grid items-center grid-cols-1 transition-all xl:grid-rows-2"
          v-bind:class="{ 'opacity-50 pointer-events-none': load }"
        >
          <div class="px-6">
            <h2
              class="mx-auto font-sans text-5xl font-light leading-none tracking-tight text-center text-gray-200 md:mx-auto"
            >
              Posts
            </h2>
          </div>
          <div class="pt-0 mt-8 xl:mt-4">
            <div class="flex w-full justify-center">
              <input
                v-model.trim="input"
                type="text"
                placeholder="Search posts"
                class="relative w-1/2 px-3 py-4 text-base text-gray-200 bg-gray-900 border-0 shadow outline-none xl:rounded bg-opacity-60 focus:outline-none focus:ring"
              >
            </div>
          </div>
        </div>
      </div>   
    </div>
  </div>    
</template>