<template>
  <v-container fluid>
    <v-layout row wrap>
      <v-flex xs12>
        <h1>Lista de Clientes</h1>
      </v-flex>
      <v-flex xs12 md6>
          <v-card dark color="teal darken-1" v-for="cliente in clientes" :key="cliente.id">
            <v-card-title primary-tittle>
              <div>
                <h3 class="headline mb-0">{{ cliente.nombre }}  {{ cliente.apellido }}</h3>
                <div>Contacto: {{ cliente.telefono }}</div>
              </div>
            </v-card-title>
          </v-card>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
import { clienteService } from '@/services/Cliente.service'
export default {
  data () {
    return {
      clientes: []
    }
  },
  mounted () {
    let vm = this
    clienteService.query().then(data => {
      vm.clientes = data.body
      console.log(data)
    }, erro => {
      console.log(erro)
    })
  }
}
</script>

