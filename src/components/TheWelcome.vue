<script>
export default {
  data() {
    return {
      listsuhu: [],
    }
  },
  methods:{
   
   async ambildata() {
     const response = await fetch("http://localhost:3000/getlist");
     const data = await response.json();
     this.listsuhu = data.sensor_suhu;
     console.log( this.listsuhu[0] );
   }
 }

}


</script>


<template>
  <table class="p-10">
    <tr>
      <td>Waktu</td>
      <td>suhu</td>
    </tr>
    <tr v-for="item in listsuhu">
      <td>{{ item.waktu }}</td>
      <td>{{ item.suhu }}</td>
    </tr>
  </table>
  <div>
    <button class="rounded hover:rounded-lg bg-blue-600 text-white" @click="ambildata()">Ambil Data</button>
  </div>
</template>
