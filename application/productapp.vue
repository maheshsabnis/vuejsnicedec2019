<template>
   <div class="container">
       <div class="form-group">
           <label>ProductRowId</label>
           <input type="text" v-model="ProductRowId" class="form-control">
       </div>
        <div class="form-group">
           <label>ProductId</label>
           <input type="text" v-model="ProductId" class="form-control">
       </div>
        <div class="form-group">
           <label>ProductName</label>
           <input type="text" v-model="ProductName" class="form-control">
       </div>
        <div class="form-group">
           <label>Category Name</label>
           <select v-model="CategoryName" class="form-control">
               <option v-for="cat in Categories" :key="cat" v-bind:value="cat">{{cat}}</option>
           </select>
       </div>
        <div class="form-group">
           <label>Manufacturer</label>
           <select v-model="Manufacturer" class="form-control">
             <option v-for="man in Manufacturers" :key="man" v-bind:value="man">{{man}}</option>   
           </select>
       </div>
         <div class="form-group">
           <label>Description</label>
           <textarea v-model="Description" class="form-control"></textarea>
       </div>
         <div class="form-group">
           <label>Base Price</label>
           <input type="text" v-model="BasePrice" class="form-control">
       </div>
       <div class="form-group">
           <input type="button" value="Clear" @click="clear()" class="btn btn-warning">
           <input type="button" value="Save" @click="addProduct()" class="btn btn-success">
       </div>
       <hr>
       <table class="table table-bordered table-striped">
           <thead>
               <tr>
                   <th>Product Row Id</th>
                   <th>Product Id</th>
                   <th>Product Name</th>
                   <th>Category Name</th>
                   <th>Manufacturer</th>
                   <th>Description</th>
                   <th>Base Price</th>   
               </tr>
           </thead>
           <tbody>
               <tr v-for="p in Products" :key="p.ProductRowId" @click="getSelectedProduct(p)">
                   <td>{{p.ProductRowId}}</td>
                   <td>{{p.ProductId}}</td>
                   <td>{{p.ProductName}}</td>
                   <td>{{p.CategoryName}}</td>
                   <td>{{p.Manufacturer}}</td>
                   <td>{{p.Description}}</td>
                   <td>{{p.BasePrice}}</td>
               </tr>
           </tbody>
       </table>
   </div>
</template>
<script>
export default {
    name:'ProductAppComponent',
    data: function(){
        return {
            ProductRowId:0,
            ProductId:'',
            ProductName:'',
            CategoryName:'',
            Manufacturer:'',
            Description: '',
            BasePrice:0,
            Categories:['Electronics','Electrical','Food'],
            Manufacturers:['HP','Bajaj','Parle'],
            Products:[]
        }
    },
    methods:{
        clear: function(){
            this.ProductRowId=0;
            this.ProductId='';
            this.ProductName='';
            this.CategoryName='';
            this.Manufacturer='';
            this.Description= '';
            this.BasePrice=0;
        },
        addProduct: function(){
            this.Products.push({
                ProductRowId:this.ProductRowId,
                ProductId:this.ProductId,
                ProductName:this.ProductName,
                CategoryName:this.CategoryName,
                Manufacturer:this.Manufacturer,
                Description: this.Description,
                BasePrice:this.BasePrice,
            });
        },
        getSelectedProduct: function(p) {
             this.ProductRowId=p.ProductRowId;
                this.ProductId=p.ProductId;
                this.ProductName=p.ProductName;
                this.CategoryName=p.CategoryName;
                this.Manufacturer=p.Manufacturer;
                this.Description=p.Description;
                this.BasePrice=p.BasePrice;
        }
    }
}
</script>