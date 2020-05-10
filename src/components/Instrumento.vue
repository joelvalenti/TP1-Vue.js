<template>
  <div class="mt-4">
    <b-card :img-src="'/images/' + instrumentoParam.imagen" img-left img-width="20%" class="mb-3">
      <b-card-title :title="instrumentoParam.instrumento"></b-card-title>
      <b-card-text>
        <h4 :precio="instrumentoParam.precio">Precio: {{instrumentoParam.precio}}</h4>
        <h4
          :cantidadVendida="instrumentoParam.cantidadVendida"
        >Cant. Vendida: {{instrumentoParam.cantidadVendida}}</h4>
        <h4 v-if="instrumentoParam.costoEnvio == 'G'" style="color:green">
          <img :src="'/images/camion.png'" width="5%"/>
          Envio gratis a todo el país 
        </h4>
        <h4 v-else style="color:orange">
          Costo de Envio Interior de Argentina: ${{ instrumentoParam.costoEnvio }}
        </h4>
      </b-card-text>
      <div style="text-align:center">
        <b-button :href="'/detalle/' + instrumentoParam.id" variant="primary" style="width:100%">
          <b>Detalle</b>
        </b-button>
      </div>
    </b-card>
  </div>
</template>
<script>
export default {
  props: ["instrumentoParam"]
};
</script>
<style lang=""></style>