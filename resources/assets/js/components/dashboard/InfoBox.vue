<template>
  <div class="wrap">
    <div class="row" v-if="isLoading">
      <h1 style="text-align:center">Cargando......</h1>
    </div>

    <div class="row clearfix" v-if="!isLoading">
      <div class="col-lg-3 col-md-3 col-sm-6 col-xs-12">
        <div class="info-box bg-teal hover-zoom-effect">
          <div class="icon">
            <i class="material-icons">contacts</i>
          </div>
          <div class="content">
            <div class="text">Clientes</div>
            <div class="number">{{ info.total_customer }}</div>
          </div>
        </div>
      </div>

      <div class="col-lg-3 col-md-3 col-sm-6 col-xs-12">
        <div class="info-box bg-orange hover-zoom-effect">
          <div class="icon">
            <i class="material-icons">people</i>
          </div>
          <div class="content">
            <div class="text">Proveedores</div>
            <div class="number">{{ info.total_vendor }}</div>
          </div>
        </div>
      </div>

      <div class="col-lg-3 col-md-3 col-sm-6 col-xs-12">
        <div class="info-box bg-deep-purple hover-zoom-effect">
          <div class="icon">
            <i class="material-icons">category</i>
          </div>
          <div class="content">
            <div class="text">Productos</div>
            <div class="number">{{ info.total_product }}</div>
          </div>
        </div>
      </div>

      <div class="col-lg-3 col-md-3 col-sm-6 col-xs-12">
        <div class="info-box bg-blue-grey hover-zoom-effect">
          <div class="icon">
            <i class="material-icons">receipt</i>
          </div>
          <div class="content">
            <div class="text">Facturas</div>
            <div class="number">{{ info.total_invoice }}</div>
          </div>
        </div>
      </div>
</template>

<script>
import { EventBus } from "../../vue-asset";
import mixin from "../../mixin";
export default {
  data() {
    return {
      info: {},
      isLoading: true,
    };
  },

  created() {
    this.getData();
  },
  methods: {
    getData() {
      axios.get(base_url + "info-box").then((response) => {
        this.info = response.data;
        this.isLoading = false;
      });
    },
  },
};
</script>