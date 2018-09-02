<template>
  <v-container>
  <div class="instrument">
    <h1>This is an instrument Search Page</h1>

    <v-form>
      <v-container>
        <v-layout row wrap>
          <v-flex xs12 sm6>
          <v-text-field
            v-model='ric'
            label="RIC"
            required
          ></v-text-field>
          </v-flex>
          <v-flex xs12 sm6>
          <v-text-field
            v-model="isin"
            label="ISIN"
            required
          ></v-text-field>
          </v-flex>
          <v-flex xs12 sm6>
          <v-text-field
            v-model="exchange"
            label="Exchange"
            required
          ></v-text-field>
          </v-flex>
          <v-flex xs12 sm3>
                    <v-text-field
            v-model="securityType"
            label="SecurityType"
            required
          ></v-text-field>
          </v-flex>
          <v-flex xs12 sm3>
          <v-text-field
            v-model="sourceSystem"
            label="Source System"
            required
          ></v-text-field>
          </v-flex>
          <v-flex xs12 sm3>
            <v-btn @click="submit">submit</v-btn>
            <v-btn @click="clear">clear</v-btn>
          </v-flex>
        </v-layout>
      </v-container>
    </v-form>
  </div>
  <div>
    <v-container>
      <v-flex xs12 sm12>
    <ag-grid-vue style="width: 100%; height: 500px;"
                 class="ag-theme-material"
                 :columnDefs="columnDefs"
                 :rowData="rowData"
                 :enableSorting="true"
                 :enableFilter="true">
    </ag-grid-vue>
      </v-flex>
    </v-container>
    </div>
  </v-container>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import { AgGridVue } from 'ag-grid-vue';
import { Grid, GridOptions, ColumnController } from 'ag-grid/main';

// import HelloWorld from '@/components/HelloWorld.vue'; // @ is an alias to /src

@Component({
  components: {
    AgGridVue,
  },
})
export default class InstrumentSearch extends Vue {

  public ric: string = '';
  public isin: string = '';
  public exchange: string = '';
  public securityType: string = '';
  public sourceSystem: string = '';

  public columnDefs = [
                {headerName: 'RIC', field: 'ric'},
                {headerName: 'ISIN', field: 'isin'},
                {headerName: 'Exchange', field: 'exchange'},
                {headerName: 'SecurityType', field: 'securityType'},
                {headerName: 'Source System', field: 'sourceSystem'},
              ];

  public rowData = [
                {ric: 'Toyota', isin: 'Celica', exchange: 'ASX', securityType: 'FUTURE', sourceSystem: 'SDS'},
                {ric: 'Ford', isin: 'Mondeo', exchange: 'ASX', securityType: 'FUTURE', sourceSystem: 'SDS'},
                // {make: 'Porsche', model: 'Boxter', price: 72000},

            ];

  private gridOptions: GridOptions = {} as GridOptions;


  constructor() {
    super();

    // let eGridDiv:HTMLElement = <HTMLElement>document.querySelector('#myGrid');
    // new Grid(eGridDiv, this.gridOptions);
  }

  public submit() {

  }

  public clear() {

  }
  /*public columnDefs() {
    return [
                {headerName: 'Make', field: 'make'},
                {headerName: 'Model', field: 'model'},
                {headerName: 'Price', field: 'price'},
              ];
  }*/


}
</script>