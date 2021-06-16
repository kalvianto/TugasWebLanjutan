<template>
  <div>
      <h1>Berikut adalah semua pengguna kita</h1>
      <ul>
        <li v-for="item in user" :key="item.id">{{item.nama}} <button @click="hapus(item.id)">X</button></li>
      </ul>
      <input v-model="username"/>
      <input v-model="password"/>
      <button @click="tambah">Add</button>
  </div>
</template>

<script>
  import axios from 'axios'
  export default{
    data:function(){ 
      return {
        user:[],
        username:'',
        password:''
      }
  },
  created: function(){
    const username = localStorage.getItem('usr')
    const password = localStorage.getItem('pwd')
    
    axios.get('http://localhost:3000/user',{headers:{username,password}}).then(result=>{
        this.users= result.data
    })
  },
  methods:{
    
    tambah: function (){
      const username = localStorage.getItem('usr')
      const password = localStorage.getItem('pwd')
      let newItem = {username:this.username, password : this.password}

      axios.post('http://localhost:3000/user',newItem,{headers:{username,password}})
      this.user.push(newItem)
    },
    hapus:function(id){
      const username = localStorage.getItem('usr')
      const password = localStorage.getItem('pwd')

      this.user = this.user.filter((user)=>user.id !== id )
      axios.delete(`http://localhost:3000/user/${id}`,{headers:{username,password}})
    }
  }
}
</script>