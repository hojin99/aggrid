<template>
  <ag-grid-vue id="grid" class="ag-theme-alpine"
    :columnDefs="columnDefs"
    :rowData="rowData">
    
  </ag-grid-vue>

</template>

<script>
import {AgGridVue} from "ag-grid-vue";

export default {
  name: 'HelloWorld',
  components: {
    AgGridVue
  },
  data() {
    return {
      columnDefs: null,
      rowData : null
    }
  },
  props: {
    msg: String
  },
  beforeMount() {
    this.columnDefs = [
      { field: "make" },
      { field: "model" },
      { field: "price" },      
    ];

    this.rowData = [
      { make: "Toyota", model: "Celica", price: 35000 },
      { make: "Ford", model: "Mondeo", price: 32000 },
      { make: "Porsche", model: "Boxter", price: 72000 },
    ];
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  #grid {
    width: 700px;
    height: 500px;
  }


</style>
