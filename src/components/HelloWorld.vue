<template>
  <div>
    <v-btn @click="getSelectedRows()"
      elevation="2"
    >Show Selected Data</v-btn>

    <ag-grid-vue id="grid" class="ag-theme-alpine"
      :columnDefs="columnDefs"
      :rowData="rowData"
      @grid-ready="onGridReady">
      
    </ag-grid-vue>
  </div>
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
      rowData : null,
      gridApi: null,
      columnApi: null,
    }
  },
  props: {
    msg: String
  },
  beforeMount() {
    this.columnDefs = [
      { field: "make", sortable: true, filter: true, checkboxSelection: true },
      { field: "model", sortable: true, filter: true },
      { field: "price", sortable: true, filter: true },      
    ];

    fetch('https://www.ag-grid.com/example-assets/small-row-data.json')
      .then(result => result.json())
      .then(rowData => this.rowData = rowData);
  },
  methods: {
    onGridReady(params) {
      console.log(params);
      this.gridApi = params.api;
      this.columnApi = params.columnApi;
    },
    getSelectedRows() {

      const selectedNodes = this.gridApi.getSelectedNodes();
      const selectedData = selectedNodes.map( node => node.data);
      const selectdDataStringPresetation = selectedData.map(node => `${node.make} ${node.model}`).join(', ');
      alert(`Selected nodes: ${selectdDataStringPresetation}`);
    }
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
