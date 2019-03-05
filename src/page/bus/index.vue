<template>
  	<div class="home_container">
        <child1 :content1="child1"></child1>
        <child2 :content1="child2"></child2>
    </div>
</template>

<script>
import Vue from 'vue'
Vue.prototype.bus = new Vue();
var child1 = {
    props: {
        content1: String
    },
    template: '<div @click="handleClick1">{{content1}}</div>',
    methods: {
        handleClick1: function() {
            console.log(this.content1)
            this.bus.$emit('change1', this.content1);
        }
    },
    mounted: function() {
      
    }
}
var child2 = {
    props: {
        content1: String
    },
    template: '<div @click="handleClick1">{{content1}}</div>',
    methods: {
        handleClick1: function() {
            console.log(this.content1)
            this.bus.$emit('change2', 'child2','213');
        }
    },
    mounted: function() {
        
    }
}

export default {
	name: 'bus',
  	components: {
          child1,
          child2
    },
    data() {
        return {
            child1: 'Hello World',
            child2: 'Hello'
        }
    },
    created(){
        // this.$set(this.someObject,'b','sally')
    },
    mounted: function () {
         this.bus.$on('change1', (msg) =>{
            console.log()
            this.child2 = msg;
        });
        this.bus.$on('change2', (msg,msg2) =>{
            console.log(msg,msg2)
            this.child1 = msg+msg2;
        });
    }
}
</script>

<style lang="less" scoped>
    *{
        color: white;
    }
</style>
