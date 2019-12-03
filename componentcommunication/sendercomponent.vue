<template>
    <div>
        <table class="table table-bordered table-striped">
            <thead>
                <tr>
                    <td>CatId</td>
                    <td>CatName</td>
                </tr>
            </thead>
            <tbody>
                <tr v-for="cat in categories" :key="cat.CatId" @click="onRowClicked(cat)">
                    <td>{{cat.CatId}}</td>
                    <td>{{cat.CatName}}</td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
import {Categories} from './models';
import {EventBus} from './../main';
export default {
    name:"SenderComponent",
    data:function(){
        return{
            categories:Categories
        } 
    },
    methods:{
        onRowClicked:function(c){
        //    console.log(`Selected Cat Id ${c.CatId}`);
            let CatId = c.CatId;
            EventBus.$emit('cat_send',CatId);
        }
    }
}
</script>