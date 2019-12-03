<template>
    <div>
     <table class="table table-bordered table-striped">
            <thead>
                <tr>
                    <td>PrdId</td>
                    <td>ProdName</td>
                    <td>Price</td>
                    <td>CatId</td>
                </tr>
            </thead>
            <tbody>
                <tr v-for="prd in filteredProducts" :key="prd.PrdId">
                    <td>{{prd.ProdId}}</td>
                    <td>{{prd.ProdName}}</td>
                    <td>{{prd.Price}}</td>
                    <td>{{prd.CatId}}</td>
                </tr>
            </tbody>
        </table>    
    </div>
</template>

<script>
import {Products} from './models';
import {EventBus} from './../main';
export default {
    name: 'ReceiverComponent',
    data:function(){
        return {
            products:Products,
            filteredProducts:[]
        }
    },
    mounted:function() {
        EventBus.$on('cat_send', (CatId)=>{
          //  console.log(`Data Received ${CatId}`);
            if(CatId > 0) {
             //   console.log('In If');
             //   console.log(`Products ${JSON.stringify(this.products)}`);
                  this.filteredProducts = this.products.filter((p,i)=>{
                      return p.CatId == CatId;
                  }); 
             //     console.log(`Filter Products ${JSON.stringify(this.filteredProducts)}`);
            }else{
             //   console.log('In else');

                this.filteredProducts = this.products;
              //  console.log(`Filter Products in Else ${this.filteredProducts}`);
            }
        });
    },
}
</script>