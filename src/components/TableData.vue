<template>
    <div>
        <table class="table">
  <thead>
    <tr>
    
      <th scope="col">nombre</th>
      <th scope="col">correo</th>
      <th scope="col">edad</th>
       <th scope="col">ciudad</th>
    </tr>
  </thead>
  <tbody>
    <tr v-for="usuario in usuarios" :key="usuario.index">
      <td >{{ usuario.nombre }}</td>
      <td>{{ usuario.email }}</td>
      <td>{{ usuario.edad }}</td>
      <td>{{ usuario.ciudad }}</td>
    </tr>
    
  </tbody>
</table>
    </div>
    
</template>

<script>
export default {


    name: 'TableData',
    components:{
     
    },
  

    data() {
        return {
            
        }
    },
    props:{
      usuarios:Object,
    },

    mounted() {
        
    },

    methods: {
        
    },
};
</script>

<style lang="scss" scoped>

</style>