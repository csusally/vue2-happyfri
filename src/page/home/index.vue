<template>
  	<div class="home_container">
          <span style="color: red; ">{{someObject.b}}</span>
        <itemcontainer father-component="home"></itemcontainer>
        
    </div>
</template>

<script>
import itemcontainer from '../../components/itemcontainer'

export default {
	name: 'home',
  	components: {
  		itemcontainer
    },
    data() {
        return {
            someObject: {}
        }
    },
    created(){
        this.$set(this.someObject,'b','sally')
    }
}
</script>

<style lang="less" scoped>
    .home_container{

    }
</style>
