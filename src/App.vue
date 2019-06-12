<template>
  <div id="app">
    <div class="buttn" @click="show = !show">点击一下</div>
    <table v-if="!show">
      <tr>
        <td>IMEI</td>
        <td>device</td>
        <td>message</td>
        <td>tel</td>
        <td>createdAt</td>
      </tr>
      <tr v-for="index in syk" :key="index">
        <td>{{index.IMEI}}</td>
        <td>{{index.device}}</td>
        <td>{{index.message}}</td>
        <td>{{index.tel}}</td>
        <td>{{index.createdAt}}</td>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  data(){
    return{
      show: true,
      syk:''
    }
  },
  created(){
    this.axios.get('http://localhost:60020/all').then((response) => {
      // console.log(response.data.data[0])
      this.syk=response.data.data
    })
  }
}
</script>


<style lang="scss">
  #app{
    .buttn{
      width: 200px;
      height: 50px;
      border-radius: 30px;
      background: #0ecaff;
      text-align: center;
      line-height: 50px;
      color: #ffffff;
      font-weight: bold;
      cursor: pointer;
      margin: 0 auto;
    }
    table{
      border: 1px solid red;
      border-radius: 5px;
      margin: 0 auto;
      margin-top: 20px;
      text-align: center;
      tr{
        border: 1px solid red;
        border-radius: 5px;
        td{
          border: 1px solid red;
        }
      }
    }
  }
</style>
