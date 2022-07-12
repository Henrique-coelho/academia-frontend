<template>
  <v-app>
    <v-app-bar app color="black" dark >
      <div class="d-flex align-center">
        <v-img alt="Gym Logo" class="shrink mr-2" contain
          src="https://www.clipartmax.com/png/full/249-2496075_learn-how-to-draw-a-pokeball-icon-in-adobe-illustrator-pokemon-gym.png"
          transition="scale-transition" width="40" @click="goToHome()"/>

        <v-img alt="Gym Name" class="shrink mt-1 hidden-sm-and-down mr-1 " contain min-width="100"
          src="https://www.coolgenerator.com/Data/Textdesign/202207/5a8c226116991f9ad77617ad231053e4.png" width="100" @click="goToHome()" />

        <v-img alt="Gym Name" class="shrink mt-1 hidden-sm-and-down mr-15" contain min-width="50"
          src="https://www.coolgenerator.com/Data/Textdesign/202207/b2f1bfb52042cfe8901f96e720dcb622.png" width="100" @click="goToHome()" />
      </div>

      <v-divider class="mx-4"></v-divider>

      <v-btn @click="goToHome()" target="_blank" text>
        <span class="mr-10">Home</span>
      </v-btn>

      <v-btn @click="goToLogin()" target="_blank" text>
        <span class="mr-10">Login</span>
      </v-btn>

      <v-btn @click="goToCadastro()" target="_blank" text>
        <span class="mr-10">Cadastro</span>
      </v-btn>
      
      <v-btn @click="goToPlanos()" target="_blank" text>
        <span class="mr-10">Planos</span>
      </v-btn>

      <v-spacer></v-spacer>

      <v-btn class="ml-10" color="error" large raised @click="retornar()">
        Sair da conta
      </v-btn>
    </v-app-bar>

    <v-main>
      <router-view />
    </v-main>
  </v-app>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  name: 'App',

  data: () => ({
    //
  }),
  methods: {
    goToHome() {
      this.$router.push('/');
    },
    goToLogin() {
      this.$router.push('/login');
    },
    goToCadastro() {
      this.$router.push('/cadastro');
    },
    goToPlanos() {
      this.$router.push('/planos');
    },
    retornar() {
      this.$router.push('/');
    }
  }
})
</script>
