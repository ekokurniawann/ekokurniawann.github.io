<template>
  <div class="h-screen flex justify-center items-center">
    <div
      class="hidden md:block lg:w-1/3 bg-white h-full auth-background rounded-tr-lg rounded-br-lg"
    ></div>
    <div class="w-auto md:w-2/4 lg:w-2/3 flex justify-center items-center">
      <div class="w-full lg:w-1/2 px-10 lg:px-0">
        <h2 class="font-normal mb-6 text-3xl text-white">Buat Akun</h2>
        <div class="mb-6">
          <div class="mb-4">
            <label class="font-normal text-lg text-white block mb-3"
              >Nama Lengkap</label
            >
            <input
              type="text"
              class="auth-form focus:outline-none focus:bg-purple-hover focus:shadow-outline focus:border-purple-hover-stroke focus:text-gray-100"
              placeholder="Tulis Nama Lengkap Anda Disini"
              v-model="register.name"
            />
          </div>
        </div>
        <div class="mb-6">
          <div class="mb-4">
            <label class="font-normal text-lg text-white block mb-3"
              >Pekerjaan</label
            >
            <input
              type="text"
              class="auth-form focus:outline-none focus:bg-purple-hover focus:shadow-outline focus:border-purple-hover-stroke focus:text-gray-100"
              placeholder="Tulis pekerjaan Anda disini"
              v-model="register.occupation"
            />
          </div>
        </div>
        <div class="mb-6">
          <div class="mb-4">
            <label class="font-normal text-lg text-white block mb-3"
              >Alamat Email</label
            >
            <input
              type="email"
              class="auth-form focus:outline-none focus:bg-purple-hover focus:shadow-outline focus:border-purple-hover-stroke focus:text-gray-100"
              placeholder="Tulis alamat email Anda disini"
              v-model="register.email"
            />
          </div>
        </div>
        <div class="mb-6">
          <div class="mb-4">
            <label class="font-normal text-lg text-white block mb-3"
              >Kata Sandi</label
            >
            <input
              type="password"
              class="auth-form focus:outline-none focus:bg-purple-hover focus:shadow-outline focus:border-purple-hover-stroke focus:text-gray-100"
              placeholder="Ketik kata sandi Anda disini"
              v-model="register.password"
              @keyup.enter="userRegister"
            />
          </div>
        </div>
        <div class="mb-6">
          <div class="mb-4">
            <button
              @click="userRegister"
              class="block w-full bg-orange-button hover:bg-green-button text-white font-semibold px-6 py-4 text-lg rounded-full"
            >
              Lanjutkan Pendaftaran
            </button>
          </div>
        </div>
        <div class="text-center">
          <p class="text-white text-md">
            Sudah punya akun?
            <nuxt-link to="/login" class="no-underline text-orange-button"
              >Masuk</nuxt-link
            >.
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  layout: 'auth',
  data() {
    return {
      register: {
        name: '',
        email: '',
        occupation: '',
        password: '',
      },
    }
  },
  methods: {
    async userRegister() {
      try {
        let response = await this.$axios.post('/api/v1/users', this.register)
        console.log(response.data.data.token)
        await this.$auth.setUserToken(response.data.data.token)
        this.$router.push({ path: '/upload' })
      } catch (error) {
        console.error(error)
      }
    },
  },
}
</script>

<style>
.auth-background {
  background-image: url('/sign-upp-background.jpg');
  background-position: center;
  background-size: cover;
}
</style>
