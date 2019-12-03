<template>
   <div id="dvParent">
       <h2>I am Parent Component</h2>
       <input type="button" value="Change Message" @click="updateMessage()">
       <ChildComponent v-bind:message="msg" @notify="onReceiveMessage"></ChildComponent>
       <hr>
       <p>Data Received from Child</p>
       <div>{{receivedMessage}}</div>   
   </div>
</template>

<script>
import ChildComponent from './ChildComponent.vue';
export default {
    name: 'ParentComponent',
    components:{
        ChildComponent
    },
    data: function(){
        return {
            msg: 'The Message from Parent',
            receivedMessage: ''
        }
    },
    methods:{
        onReceiveMessage: function(m){
            this.receivedMessage = m;
        },
        updateMessage:function(){
            this.msg = 'New Message';
        }
    }
}
</script>