<template>
  <b-container fluid>
    <b-row style="margin-right: 1%">
      <b-col>
        <img style="max-height:400px" :src="'/images/' + instrumentoEncontrado.imagen" width="80%" />
      </b-col>
      <b-col style="margin-top: 1%; margin-botton:1%; margin-right:2%">
        <b-row>
          <h4>{{instrumentoEncontrado.cantidadVendida}} vendidos</h4>
        </b-row>
        <b-row>
          <h1>{{ instrumentoEncontrado.instrumento }}</h1>
        </b-row>
        <b-row>
          <h1>$ {{ instrumentoEncontrado.precio }}</h1>
        </b-row>
        <b-row>
          <h3>Marca: {{ instrumentoEncontrado.marca }}</h3>
        </b-row>
        <b-row>
          <h3>Modelo: {{ instrumentoEncontrado.modelo }}</h3>
        </b-row>
        <b-row>
          <div v-if="instrumentoEncontrado.costoEnvio == 'G'">
            <img :src="'/images/camion.png'" width="12%" />
            <span style="color:green; font-size: 140%"> Envío gratis a todo el país</span>
          </div>
          <div v-else>
            <h3 style="color:orange">Costo de Envio Interior de Argentina: ${{ instrumentoEncontrado.costoEnvio }}</h3>
          </div>
        </b-row>
        <b-row style="text-align:center">
          <b-button href="/" variant="outline-primary" style="width: 30%; margin-top:1%">Agregar al carrito</b-button>
        </b-row>
      </b-col>
      <b-row>
        <h3
          style="margin-left: 3%; margin-top:1%; margin-right:10%"
        >Descripción: {{ instrumentoEncontrado.descripcion }}</h3>
      </b-row>
    </b-row>
  </b-container>
</template>

<script>
export default {
  name: "DetalleInstrumento",
  components: {},
  mounted() {
    this.getInstrumentoXId();
  },
  data() {
    return {
      instrumentoEncontrado: []
    };
  },
  methods: {
    async getInstrumentoXId() {
      const parametroId = this.$route.params.id;
      const res = await fetch("/instrumentos.json");
      const resJson = await res.json();
      console.log(resJson);
      this.instrumentoEncontrado = await resJson.instrumentos.find(
        instrumento => instrumento.id === parametroId
      );
      console.log(this.instrumentoEncontrado);
    }
  }
};
</script>
