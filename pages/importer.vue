<template>
  <div>
    <div class="header">
      <div class="flex h-16">
        <div class="m-auto">
          <h2 class="max-w-lg my-6 font-sans text-3xl font-bold leading-none tracking-tight text-gray-200 sm:text-4xl sm:mx-auto">Import from Paysite</h2>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
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
    }
  }
}
</script>
