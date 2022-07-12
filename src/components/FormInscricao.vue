<template>
  <v-container>
    <v-form>
      <v-row class="my-10"></v-row>
      <v-card class="mx-auto my-12" max-width="500">
        <v-card-title>Dados necessários</v-card-title>
        <v-row class="mx-auto">
          <v-col>
            <v-text-field v-model="dados.nome" label="Nome*" required>
            </v-text-field>
          </v-col>
        </v-row>
        <v-row class="mx-auto">
          <v-col>
            <v-text-field v-model="dados.sobrenome" label="Sobrenome*" required></v-text-field>
          </v-col>
        </v-row>
        <v-row class="mx-auto">
          <v-col>
            <v-text-field v-model="dados.cpf" label="CPF*" required></v-text-field>
          </v-col>
        </v-row>
        <v-row class="mx-auto">
          <v-col>
            <v-text-field v-model="dados.cep" label="CEP*" required></v-text-field>
          </v-col>
        </v-row>
        <v-btn @click="getCEP()" text>
          <span class="mr-10">Buscar CEP</span>
        </v-btn>
        <v-row class="mx-auto">
          <v-col>
            <v-text-field v-model="dados.logradouro" label="Rua*" disabled></v-text-field>
          </v-col>
        </v-row>
        <v-row class="mx-auto">
          <v-col>
            <v-text-field v-model="dados.numero" label="Numero*" required></v-text-field>
          </v-col>
        </v-row>
        <v-row class="mx-auto">
          <v-col>
            <v-text-field v-model="dados.uf" label="Estado*" disabled></v-text-field>
          </v-col>
        </v-row>
        <v-row class="mx-auto">
          <v-col>
            <v-text-field v-model="dados.localidade" label="Cidade*" disabled></v-text-field>
          </v-col>
        </v-row>
        <v-row class="mx-auto">
          <v-col>
            <v-text-field v-model="dados.complemento" label="Complemento*" required></v-text-field>
          </v-col>
        </v-row>
        <v-row>
          <v-col class="text-center">
            <v-btn class="mr-auto" color="primary" elevation="2" large raised>
              Continuar
            </v-btn>
            <v-btn class="mx-auto ml-7" type="button" variant="outline-secondary" large>
              Retornar
            </v-btn>
          </v-col>
        </v-row>
      </v-card>
    </v-form>
  </v-container>
</template>
<script lang="ts">
import Vue from 'vue'
import axios from 'axios'

Vue.prototype.$http = axios;

export default Vue.extend({
  name: 'FormInscricao',
  components: {
  },

  data: () => ({
    posts: [],
    dados: { nome: '', sobrenome: '', cpf: '', cep: '', logradouro: '', numero: '', uf: '', localidade: '', complemento: '' },
    text: '',
  }),

  methods: {
    getCEP() {
      axios
        .post("http://viacep.com.br/ws/" + this.dados.cep + "/json/")
        .then((res) => {
          this.dados.logradouro = res.data.nome
          this.dados.numero = res.data.numero
          this.dados.uf = res.data.uf
          this.dados.localidade = res.data.localidade
          this.dados.complemento = res.data.complemento
        }).catch((error) => {
          this.text = 'Erro ao realizar cadastro!'
          console.log(error)
        })
    }
  }

})
</script>
