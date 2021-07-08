<template>
  <!-- This is an example component -->
  <div class="h-screen font-sans login bg-cover">
    <div
      class="container mx-auto h-full flex flex-1 justify-center items-center"
    >
      <div class="w-full max-w-lg">
        <div class="leading-loose">
          <form
            class="max-w-sm m-4 p-10 bg-white bg-opacity-25 rounded shadow-xl"
            @submit.prevent="onSubmit()"
          >
            <p class="text-white font-medium text-center text-lg font-bold">
              LOGIN
            </p>
            <div class="">
              <label class="block text-sm text-white" for="email">E-mail</label>
              <input
                id="email"
                v-model="email"
                class="w-full px-5 py-1 text-gray-700 bg-gray-300 rounded focus:outline-none focus:bg-white"
                type="email"
                placeholder="Email"
                aria-label="email"
                required
              >
            </div>
            <div class="mt-2">
              <label class="block text-sm text-white">Contraseña</label>
              <input
                id="password"
                v-model="password"
                class="w-full px-5 py-1 text-gray-700 bg-gray-300 rounded focus:outline-none focus:bg-white"
                type="password"
                placeholder="Contraseña"
                arial-label="password"
                required
              >
            </div>

            <div class="mt-4 items-center flex justify-between">
              <button
                class="px-4 py-1 text-white font-light tracking-wider bg-gray-900 hover:bg-gray-800 rounded"
                type="submit"
              >
                Entrar
              </button>
              <a
                class="inline-block right-0 align-baseline font-bold text-sm text-500 text-white hover:text-red-400"
                href="#"
              >¿Olvidó su contraseña?</a>
            </div>
            <div class="text-center">
              <a
                class="inline-block right-0 align-baseline font-light text-sm text-500 hover:text-red-400"
              >
                Crear una cuenta
              </a>
            </div>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  auth: 'guest',
  data () {
    return {
      email: 'admin@admin.com',
      password: 'password'
    }
  },
  methods: {
    async onSubmit () {
      await this.$auth.loginWith('laravelSanctum', {
        data: {
          email: this.email,
          password: this.password
        }
      })

      this.$router.push({
        path: 'dashboard'
      })
    }
  }
}
</script>

<style>
.login{
  background: url('http://bit.ly/2gPLxZ4');
  background-repeat: no-repeat;
  background-size: cover;
}
</style>
