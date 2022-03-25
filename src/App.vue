<template>
  <div class="containercol-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3" >
    <h1>Siembras disponibles - listar</h1>
    <hr />
    <button
      @click="showSow()"
      v-if="primerConsulta == false"
      class="btn btn-primary center"
    >
      Mostrar siembra
    </button>
    <div v-if="siembra" class="panel-siembra">
      <ElementsPanel :plantingInformation="siembra" @deletedId="deletedWithId">
      </ElementsPanel>
    </div>
    <button
      @click="showSow()"
      v-if="primerConsulta == true"
      class="btn btn-primary center"
    >
      Actualizar
    </button>
  </div>
</template>

<script>
import axios from "axios";
import ElementsPanel from "./components/ElementsPanel.vue";

export default {
  components: {
    ElementsPanel,
  },
  data() {
    return {
      siembra: "",
      primerConsulta: false
    };
  },
  methods: {
    async showSow() {
      const consulta = await axios
        .get("https://back-evergreen-pro.herokuapp.com/api/siembra")
        .then(res => {
          console.log(res);
          this.siembra = res.data;
          console.log(this.siembra);
        })
        .catch(error => console.log(error));
      this.primerConsulta = true;
    },
    deletedWithId(id) {
      let url = "https://back-evergreen-pro.herokuapp.com/api/siembra/" + id;
      axios
        .delete(url)
        .then(res => console.log(rest))
        .catch(error => console.log(error));
      console.log("From App", url);
    }
  }
};
</script>

<style scoped>
button {
  margin: 10px;
}

.center {
  margin: auto;
  padding: 10px;
  text-align: center;
}
</style>
