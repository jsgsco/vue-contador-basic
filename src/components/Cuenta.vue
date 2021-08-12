<template>
  <h2>Tipo de Cuenta: {{ cuenta }}</h2>
  <h2>Saldo: {{ saldo }}</h2>
  <h2>Cuenta {{ estado ? 'Activa' : 'Desactivada' }}</h2>
  <div v-for="(item, index) in servicios" :key="index">
     {{ index + 1 }} - {{ item }}
  </div>
  <AccionSaldo 
    texto="Aumentar Saldo"
    @accion="aumentar"
  />
  <AccionSaldo 
    texto="Disminuir Saldo"
    @accion="disminuir"
    :desactivar="desactivar"
  />
</template>

<script>
import AccionSaldo from './AccionSaldo.vue'

export default {
    name: 'Cuenta',
    components: {
        AccionSaldo
    },
    data() {
        return {
            cuenta: 'Visa',
            saldo: 0,
            estado: true,
            servicios: ['Giro', 'Abono', 'Transferencia'],
            desactivar: false
        }
    },
    methods: {
        aumentar() {
            this.saldo = this.saldo + 100
            this.desactivar = false
        },
        disminuir() {
            if(this.saldo === 0 ) {
                this.desactivar = true
                return
            }
            this.saldo = this.saldo - 100
        }
    }
}
</script>

<style>

</style>