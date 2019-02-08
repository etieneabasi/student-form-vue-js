<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">

    <div class="container topRow">
      <div class="container">
      <div class="row topRow bg-light border d-flex align-items-center justify-content-center" >
      <button type="button" @click="fetchUsers" class="btn btn-success">Fetch Records</button>
      <button type="button" class="btn btn-success ml-2" data-toggle="modal" data-target="#exampleModal" data-whatever="@getbootstrap">Register Student</button>
     </div>
     <div class="modal fade" id="exampleModal" tabindex="-1" role="dialog" aria-labelledby="exampleModalLabel" aria-hidden="true">
      <div class="modal-dialog" role="document">
        <div class="modal-content">
          <div class="modal-header">
            <h5 class="modal-title" id="exampleModalLabel">New message</h5>
            <button type="button" class="close" data-dismiss="modal" aria-label="Close">
              <span aria-hidden="true">&times;</span>
            </button>
          </div>
          <div class="modal-body">
           <div class="  mt-1" style="">
<<<<<<< HEAD
         <form @submit.prevent="saveStudent" method="POST">
              <div class="form-group row pr-3">
                <label for="staticEmail" class="col-sm-3 col-form-label text-left">Name</label>
                <div class="col-sm-9">
                <input type="text" class="form-control-plaintext border" v-model="form.name" value=""  id="exampleInputEmail1" name="name" aria-describedby="emailHelp" placeholder="">
=======
         <form action="api" method="POST">
              <div class="form-group row pr-3">
                <label for="staticEmail" class="col-sm-3 col-form-label text-left">Name</label>
                <div class="col-sm-9">
                <input type="text" class="form-control-plaintext border" value=""  id="exampleInputEmail1" name="fName" aria-describedby="emailHelp" placeholder="">
>>>>>>> ea17944a28b2c5f480447d9be75cfd16ad271dab
                </div>
              </div>
              <div class="form-group row pr-3">
                <label for="inputPassword" class="col-sm-3 col-form-label text-left">Reg Num</label>
                <div class="col-sm-9">
<<<<<<< HEAD
                <input type="text" class="form-control-plaintext border" v-model="form.reg_no" value="" id="exampleInputPassword1" name="reg_no" placeholder="">
=======
                <input type="text" class="form-control-plaintext border" value="" id="exampleInputPassword1" name="fFirst" placeholder="">
>>>>>>> ea17944a28b2c5f480447d9be75cfd16ad271dab
                </div>
              </div>
              <div class="form-group row pr-3">
                <label for="inputPassword" class="col-sm-3 col-form-label text-left">Phone Num</label>
                <div class="col-sm-9">
<<<<<<< HEAD
                <input type="number" class="form-control-plaintext border" v-model="form.phone" value="" id="exampleInputPassword1" name="phone" placeholder="">
=======
                <input type="number" class="form-control-plaintext border" value="" id="exampleInputPassword1" name="email" placeholder="">
>>>>>>> ea17944a28b2c5f480447d9be75cfd16ad271dab
                </div>
              </div>
              <div class="form-group row pr-3">
                <label for="inputPassword" class="col-sm-3 col-form-label text-left">Email</label>
                <div class="col-sm-9">
<<<<<<< HEAD
                <input type="email" class="form-control-plaintext border mr-2" v-model="form.email" name="email" id="exampleInputPassword1" placeholder="">
=======
                <input type="email" class="form-control-plaintext border mr-2" name="pNumber" id="exampleInputPassword1" placeholder="">
>>>>>>> ea17944a28b2c5f480447d9be75cfd16ad271dab
                </div>
              </div>
               <div class="modal-footer">
              <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
<<<<<<< HEAD
              <button type="submit"  class="btn btn-success">Submit Record</button>
=======
              <button type="button" @click="submitUsers" class="btn btn-success">Submit Record</button>
>>>>>>> ea17944a28b2c5f480447d9be75cfd16ad271dab
            </div>
          </form>
         </div>
         </div>
        
    </div>
  </div>
</div>
       <div class="row d-flex justify-content-between" v-if="hasFetchedRecords">
         <div class="card p-2 mt-1 mb-2" style="" v-for="data in dataArray" :key="data.id">
           <header name="fName" class="text-success bold  font mb-3">{{hName()}}</header>
         <form>
              <div class="form-group row">
                <label for="staticEmail" class="col-sm-4 col-form-label">Name</label>
                <div class="col-sm-8">
                <input type="text" class="form-control-plaintext border" :value="data.name"  readonly id="exampleInputEmail1" name="fName" aria-describedby="emailHelp" placeholder="">
                </div>
              </div>
              <div class="form-group row">
                <label for="inputPassword" class="col-sm-4 col-form-label">Email</label>
                <div class="col-sm-8">
                <input type="text" class="form-control-plaintext border" :value="data.email"  readonly id="exampleInputPassword1" name="fFirst" placeholder="">
                </div>
              </div>
              <div class="form-group row">
                <label for="inputPassword" class="col-sm-4 col-form-label text-left">Reg Num</label>
                <div class="col-sm-8">
                <input type="email" class="form-control-plaintext border" :value="data.reg_no"  readonly id="exampleInputPassword1" name="email" placeholder="">
                </div>
              </div>
              <div class="form-group row">
                <label for="inputPassword" class="col-sm-4 col-form-label">Phone Number</label>
                <div class="col-sm-8">
                <input type="number" class="form-control-plaintext border" name="pNumber" :value="data.phone" readonly id="exampleInputPassword1" placeholder="">
                </div>
              </div>
              <button type="button" @click="deleteUsers(data.id)" class="btn btn-success">Delete Record</button>
          </form>
         </div>
       </div>
       </div>
      </div>
     </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import axios from 'axios';
const baseUrl = 'http://127.0.0.1:3000';

export default {
  name: 'app',
  data(){
      return{
        form:{},
        isloader:true,
        hasFetchedRecords: false,
        dataArray:[],
        apiData: []
      }
  },
  components: {
    // HelloWorld
  },
  methods:{
    saveStudent(event) {
      let formdata = new FormData(event.target);
      axios.post(`${baseUrl}/students`, this.form).then (res => {
        this.fetchUsers();
      })
    },
    deleteUsers(id) {
      axios.delete(`${baseUrl}/students/${id}`).then(res=> {
        this.dataArray.splice(this.dataArray.findIndex(arr => arr.id === id),1 )
      })
    },
    hName:function (){
      // return 'Hello'+' '+ apiData.name;
    },
    fetchUsers () {
      axios.get(`${baseUrl}/students`).then(res => {
        this.isloader=false;
        this.hasFetchedRecords = true;
        this.dataArray=res.data;
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
