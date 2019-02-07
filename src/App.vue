<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">

    <div class="container topRow">
      <div class="container">
      <div class="row topRow bg-light border d-flex align-items-center justify-content-center" >
      <button type="button" @click="fetchUsers" class="btn btn-success">Fetch Records</button>
      <button type="button" @click="deleteUsers" class="btn btn-success ml-3">Register Student</button>
     </div>
     <div class="row d-flex justify-content-between" >
         <div class="card p-2 mt-1 mb-2" style="">
           <!-- <header name="fName" class="text-success bold  font mb-3"></header> -->
         <form action="api" method="POST">
              <div class="form-group row">
                <label for="staticEmail" class="col-sm-4 col-form-label">Name</label>
                <div class="col-sm-8">
                <input type="text" class="form-control-plaintext border" value=""  id="exampleInputEmail1" name="fName" aria-describedby="emailHelp" placeholder="">
                </div>
              </div>
              <div class="form-group row">
                <label for="inputPassword" class="col-sm-4 col-form-label">Email</label>
                <div class="col-sm-8">
                <input type="text" class="form-control-plaintext border" value="" id="exampleInputPassword1" name="fFirst" placeholder="">
                </div>
              </div>
              <div class="form-group row">
                <label for="inputPassword" class="col-sm-4 col-form-label">Reg Num</label>
                <div class="col-sm-8">
                <input type="email" class="form-control-plaintext border" value="" id="exampleInputPassword1" name="email" placeholder="">
                </div>
              </div>
              <div class="form-group row">
                <label for="inputPassword" class="col-sm-4 col-form-label">Email</label>
                <div class="col-sm-8">
                <input type="number" class="form-control-plaintext border" name="pNumber" id="exampleInputPassword1" placeholder="">
                </div>
              </div>
              <button type="button" @click="submitUsers" class="btn btn-success">Submit Record</button>
          </form>
         </div>
         </div>
       <div class="row d-flex justify-content-between" v-if="hasFetchedRecords">
         <div class="card p-2 mt-1 mb-2" style="" v-for="apiData in dataArray" :key="apiData.id">
           <header name="fName" class="text-success bold  font mb-3">{{hName()}}</header>
         <form>
              <div class="form-group row">
                <label for="staticEmail" class="col-sm-4 col-form-label">Name</label>
                <div class="col-sm-8">
                <input type="text" class="form-control-plaintext border" value=""  readonly id="exampleInputEmail1" name="fName" aria-describedby="emailHelp" placeholder="">
                </div>
              </div>
              <div class="form-group row">
                <label for="inputPassword" class="col-sm-4 col-form-label">Email</label>
                <div class="col-sm-8">
                <input type="text" class="form-control-plaintext border" value=""  readonly id="exampleInputPassword1" name="fFirst" placeholder="">
                </div>
              </div>
              <div class="form-group row">
                <label for="inputPassword" class="col-sm-4 col-form-label">Reg Num</label>
                <div class="col-sm-8">
                <input type="email" class="form-control-plaintext border" value=""  readonly id="exampleInputPassword1" name="email" placeholder="">
                </div>
              </div>
              <div class="form-group row">
                <label for="inputPassword" class="col-sm-4 col-form-label">Email</label>
                <div class="col-sm-8">
                <input type="number" class="form-control-plaintext border" name="pNumber" readonly id="exampleInputPassword1" placeholder="">
                </div>
              </div>
              <button type="button" @click="deleteUsers" class="btn btn-success">Delete Record</button>
          </form>
         </div>
       </div>
       </div>
      </div>
     </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import axios from 'axios';
const baseUrl = 'https://jsonplaceholder.typicode.com';

export default {
  name: 'app',
  data(){
      return{
        isloader:true,
        hasFetchedRecords: false,
        dataArray:[1,2,3],
      }
  },
  components: {
    HelloWorld
  },
  methods:{
    hName:function (){
      return 'Hello'+' '+ apiData.name;
    },
    fetchUsers () {
      axios.get(`${baseUrl}/users`).then(res => {
        this.isloader=false;
        this.hasFetchedRecords = true;
        this.dataArray=res.apiData;
      })
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.topRow{
  height: 150px;
  /* width: 100%; */
}
header{
  height: 40px;
}
</style>
