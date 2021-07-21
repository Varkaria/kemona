<template>
  <div id="index">
    <EleNews />

    <div class="header">
      <div
        class="relative px-4 py-8 mx-auto mt-4 overflow-hidden shadow-lg sm:py-16 lg:rounded-xl md:max-w-full lg:max-w-screen-xl md:px-24 lg:px-8 lg:py-20"
        style="background: linear-gradient(rgb(31 41 55 / 80%), rgb(31 41 55)), url(/headers/home.jpg);"
      >
        <div class="grid lg:grid-cols-1">
          <div class="flex flex-col mx-auto mb-16 sm:justify-center sm:text-center sm:mb-0">
            <img
              class="block w-12 h-12 mb-2 rounded-lg sm:mx-auto"
              src="~/assets/logo.png"
            >
            <div class="max-w-xl mx-auto mb-10 sm:mx-auto sm:text-center md:mb-12">
              <h2
                class="max-w-lg gap-4 mb-6 font-sans text-3xl font-bold leading-none tracking-tight text-gray-200 sm:text-4xl sm:mx-auto"
              >
                Kemono
              </h2>
              <p class="text-base text-gray-300 md:text-lg">
                a scraper for Patreon, Pixiv Fanbox, SubscribeStar, Gumroad, Discord,
                DLsite, and Fantia. Contributors here upload content from paywalls, and
                share it here for easy searching and organization. To get started viewing
                paywalled content, either search for creators on the [Artists] tab, or
                search for content on the [Posts] tab.
              </p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
