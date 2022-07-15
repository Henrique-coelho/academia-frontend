<template>
    <v-container>
        <v-row class="my-5"></v-row>
        <div>
            <h1 class="my-10">Exames</h1>
        </div>
        <div>
            <v-row class="ml-10">
                <div v-for="exame in retornoExames" class="mr-5 mb-5">
                    <template>
                        <v-card outlined color="black" elevation="13" class="white--text" width="250px" height="180px">
                            <h2 class="text-center">{{ exame.nomeAluno }}</h2>
                            <h3 class="text-center">
                                Altura: {{ exame.altura }}
                            </h3>
                            <h3 class="text-center">
                                Peso: {{ exame.peso }}
                            </h3>
                            <h3 class="text-center">
                                Medico: {{ exame.nomeMedico }}
                            </h3>
                            <h3 class="text-center">
                                Descricao: {{ exame.descricao }}
                            </h3>
                            <v-row class="mt-3"></v-row>
                        </v-card>
                    </template>
                </div>
            </v-row>
        </div>
    </v-container>
</template>

<script lang="ts">
import Vue from "vue";
import axios from "axios";

export default Vue.extend({
    name: "Exame",
    data: function () {
        return {
            urlExames: "http://localhost:8080/api/exames/",
            retornoExames: [{
                "peso": 10,
                "altura": 10,
                "autorizado": true,
                "nomeAluno": "pedro",
                "nomeMedico": "augusto",
                "descricao": "ta vivo"
            }],
        };
    },
    methods: {
        BuscarExames() {
            axios
                .get(this.urlExames + "getExamesFromCPF/" + this.$route.params.id)
                .then((res) => {
                    this.retornoExames = res.data;
                }).catch((error) => {
                    console.log(error);
                });
        },
    },
    mounted() {
        this.BuscarExames();
    },
    components: {
    }
});
</script>