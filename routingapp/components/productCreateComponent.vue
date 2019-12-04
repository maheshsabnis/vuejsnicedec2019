<template>
  <div class="container" id="dv">
    <h2>Create Product</h2>
    <div class="form-group">
      <label for="ProductRowId">ProductRowId</label>
      <input type="number" v-model.number="product.ProductRowId" class="form-control" />
    </div>
    <div class="form-group">
      <label for="ProductId">ProductId</label>
      <input type="text" v-model="product.ProductId" class="form-control" />
    </div>
    <div class="form-group">
      <label for="ProductName">ProductName</label>
      <input type="text" v-model="product.ProductName" class="form-control" />
    </div>
    <div class="form-group">
      <label for="Manufacturer">Manufacturer</label>
      <select class="form-control" v-model="product.Manufacturer">
        <option v-for="man in Manufacturers" :key="man" v-bind:value="man">{{man}}</option>
      </select>
    </div>
    <div class="form-group">
      <label for="CategoryName">CategoryName</label>
      <select class="form-control" v-model="product.CategoryName">
        <option v-for="cat in Categories" :key="cat" v-bind:value="cat">{{cat}}</option>
      </select>
    </div>
    <div class="form-group">
      <label for="Description">Description</label>
      <textarea class="form-control" v-model.lazy="product.Description"></textarea>
    </div>
    <div class="form-group">
      <label for="BasePrice">BasePrice</label>
      <input type="number" v-model.number="product.BasePrice" class="form-control" />
    </div>
    <div class="form-group">
      <input type="button" value="New" v-on:click="clear" class="btn btn-warning" />
      <input type="button" value="Save" v-on:click="save" class="btn btn-success" />
    </div>
  </div>
</template>
<script>
import VueRouter from 'vue-router';
import {EventBus} from './../../main';

var Product = {
  ProductRowId: 0,
  ProductId: "",
  ProductName: "",
  Manufacturer: "",
  CategoryName: "",
  Description: "",
  BasePrice: 0
};
 
const variables = {
   router: new VueRouter()
}; 
export default {
  name: "ProductCreateComponent",
  data: function() {
    return {
      Categories: ["Electronics", "Electrical", "Food"],
      Manufacturers: ["IBM", "Bajaj", "Parle"],
      product: Product,
      products: []
    };
  },
  methods: {
    clear: function() {
      this.product.ProductRowId = 0;
      this.product.ProductId = "";
      this.product.ProductName = "";
      this.product.Manufacturer = "";
      this.product.CategoryName = "";
      this.product.Description = "";
      this.product.BasePrice = 0;
    },
    save: function() {
      alert('ddd');
        let prd  = Object.assign({}, this.product);
        this.products.push(prd);
        console.log(JSON.stringify(this.products));
        EventBus.$emit('send-data',this.product);
        this.$router.push('/'); // explicit navigation
        // pquery to the router table to navigate for a path
    } 
  }
};
</script>
