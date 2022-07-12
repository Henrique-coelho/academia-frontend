<template>
  <form-inscricao />
</template>

<script lang="ts">
import Vue from 'vue'
import FormInscricao from '../components/FormInscricao.vue'

export default Vue.extend({
  name: 'Insricao',

  components: {
    FormInscricao
  }
})
</script>
