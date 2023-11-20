<template>

            
</template>
<script>

export default {
  name: 'favoritos',
  data(){
    return{
        fav:[]
    }
  },
  methods:{
    agrCar(item){
        this.fav.push (item)
    }
   }
}
</script>
<style scoped>
    
</style>
