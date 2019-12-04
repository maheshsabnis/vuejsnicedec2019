<template>
  <div>
    <table class="table table-bordered table-striped">
           <thead>
               <tr>
                   <td v-for="h in colHeaders" :key="h">{{h}}</td>
                  <td></td>
               </tr>
           </thead>
           <tbody>
               <tr v-for="p in Products" :key="p.ProductRowId">
                     <td v-for="h in colHeaders" :key="h">{{p[h]}}</td>
                     <td>
                       <input type="button" value="Edit" @click="edit(p.ProductRowId)">
                     </td>
               </tr>
           </tbody>
       </table>
  </div>
</template>

<script>
import DynamicTableComponent from "./../../components/DynamicTableComponent.vue";
import {EventBus} from './../../main';
let Product = {
            ProductRowId:0,
            ProductId:'',
            ProductName:'',
            CategoryName:'',
            Description: '',
            BasePrice:0
};
export default {
  name: "ProductListComponent",
  components: {
    DynamicTableComponent
  },
  data: function() {
    let headers = [];
        for(let p in Product){
            headers.push(p);
        }
    return {
      Products: [
        {
          ProductRowId: 101,
          ProductId: "Prd001",
          ProductName: "Laptop",
          Manufacturere: "IBM",
          CategoryName: "Electronics",
          Description: "Gaming",
          BasePrice: 120000
        },
        {
          ProductRowId: 102,
          ProductId: "Prd002",
          ProductName: "Iron",
          Manufacturere: "Bajaj",
          CategoryName: "Electrical",
          Description: "Power",
          BasePrice: 1200
        },
        {
          ProductRowId: 103,
          ProductId: "Prd003",
          ProductName: "Parle-G",
          Manufacturere: "Parle",
          CategoryName: "Food",
          Description: "Glucose",
          BasePrice: 20
        }
      ],
      colHeaders:headers
    };
  },
  mounted:function() {
      EventBus.$on('send-data',(data)=>{
          this.Products.push(data);
          console.log(`Data Received ${JSON.stringify(this.Products)}`);
      });  
  },
  methods: {
    edit: function(id){
      // alert(id);
        this.$router.push('/productedit/' + id); 
    }
  }
};
</script>