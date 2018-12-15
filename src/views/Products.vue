<template>
  <div>
    <h1>Products List</h1>
    <b-table striped hover :items="products" :fields="fields" :per-page = "pageSize" :current-page = "pageIndex"></b-table>
    <b-pagination size="md" :total-rows="products.length" v-model="pageIndex" :per-page="pageSize">
    </b-pagination>
  </div>
</template>
<script>
import axios from 'axios'
export default {
  name: 'products',
  
  data(){
      return{
          message:'project2',
          products: [],
          pageSize: 10,
          pageIndex: 1,
          fields: [{
            key:'product_id',
            sortable : true,
            variant: 'Secondary'
          },
          {
            key:'product_name',
            sortable : true,
            variant: 'Secondary'
          },
          {
            key:'unit_price',
            sortable : true,
            variant: 'Secondary'
          }]
      }
  },
  
  mounted(){
      var instance = this
      axios
      .get('https://enigmatic-harbor-83821.herokuapp.com/api/products')
      .then(function(response){
          console.log(response.data)
          instance.products = response.data.data
      })
    }
}


</script>