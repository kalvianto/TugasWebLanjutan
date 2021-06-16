<template>
  <div>
      <h1>Berikut adalah tugas kita</h1>
      <ul>
        <li v-for="item in todos" :key="item.id">{{item.nama}} <button @click="hapus(item.id)">X</button></li>
      </ul>
      <input v-model="myText"/>
      <button @click="tambah">Add</button>
  </div>
</template>

<script>
  import axios from 'axios'
  export default{
    data:function(){ 
      return {
        todos:[],
        myText:''
      }
  },
  created: function(){
    const username = localStorage.getItem('usr')
    const password = localStorage.getItem('pwd')
    axios.get('http://localhost:3000/todo',{headers:{username,password}}).then(result=>{
        this.todos= result.data
    })
  },
  methods:{
    tambah: function (){
      const username = localStorage.getItem('usr')
      const password = localStorage.getItem('pwd')
      let newItem = {nama:this.myText}
      
      axios.post('http://localhost:3000/todo',newItem,{headers:{username,password}}).then(result=>{
          this.todos.push(newItem)
      })
    },
    hapus:function(id){
      const username = localStorage.getItem('usr')
      const password = localStorage.getItem('pwd')
      this.todos = this.todos.filter((barang)=>barang.id !== id)
      axios.delete(`http://localhost:3000/todo/${id}`,{headers:{username,password}})
    }
  }
}
</script>