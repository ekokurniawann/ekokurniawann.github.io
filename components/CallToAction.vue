<template>
  <section style="background-color: #a56d45" class="call-to-action pt-64 pb-10">
    <div class="container mx-auto">
      <div class="w-full text-center">
        <h1 class="text-5xl text-white font-semibold">
          Cara mudah untuk mendanai
          <br />
          ide terbaik dan inovasi
        </h1>
        <button
          @click="$router.push({ path: '/register' })"
          class="inline-block bg-orange-button hover:bg-green-button text-white font-semibold px-6 py-4 mt-8 text-lg rounded-full"
        >
          Mulai Sekarang
        </button>
      </div>
    </div>
  </section>
</template>
