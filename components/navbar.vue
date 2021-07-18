<template>
  <!-- This example requires Tailwind CSS v2.0+ -->
  <nav class="bg-gray-800">
    <div class="px-2 mx-auto max-w-7xl sm:px-6 lg:px-8">
      <div class="relative flex items-center justify-center h-16">
        <div
          class="flex items-center flex-1 sm:items-stretch sm:justify-start"
        >
          <div class="flex items-center flex-shrink-0">
            <img
              class="block w-auto h-8 rounded-lg"
              src="~/assets/logo.png"
              alt="Workflow"
            >
          </div>
          <div class="hidden sm:block sm:ml-6">
            <div class="flex space-x-4">
              <a
                href="#"
                class="px-3 py-2 text-sm font-medium text-gray-300 rounded-md hover:bg-gray-700 hover:text-white"
                aria-current="page"
              >Artists</a>

              <a
                href="#"
                class="px-3 py-2 text-sm font-medium text-gray-300 rounded-md hover:bg-gray-700 hover:text-white"
              >Posts</a>

              <a
                href="#"
                class="px-3 py-2 text-sm font-medium text-gray-300 rounded-md hover:bg-gray-700 hover:text-white"
              >Requests</a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </nav>
</template>
