<template>
   <div id="dvChild">
       <h2>I am Child Component</h2>
       <input type="button" value="Send Message" @click="display">
       <div>
           <span>
               {{message}}
           </span>
       </div>
   </div>
</template>

<script>
// the child component uses the 'props' object to define
// input binding properties aka properties uses across components
// for communication. E.g. when the component is used inside the parent
// input binding will be used as v-bind:<PROPS-NAME>, v-bind:message
export default {
    name: 'ChildComponent',
    props:{
        // property map for the props so that mounting can initialize the value
        message:String 
    },
    created(){
        console.log('Component Created');
    },
    mounted(){
        console.log('Component Mounted');
    },
    data: function(){
        return {
            sendMessage:''
        }
    },
    methods:{
        display: function(){
            alert('Message from Child Component');
            this.sendMessage = 'Hay Parent, I am comming from child...';
            // the 'notify' is an event that will be emitted by the
            // current component
            this.$emit('notify',this.sendMessage);
        }
    }
}
</script>