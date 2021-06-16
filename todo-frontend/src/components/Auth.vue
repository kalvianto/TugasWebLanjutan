<template>
    <div>
        <div>
            <label>username</label>
            <input type="text" v-model="username"/>
        </div>
        <div>
            <label>password</label>
            <input type="password" v-model="password"/>
        </div>
        <button @click="simpan">Save</button>
        <button @click="hapus">Delete</button>
    </div>
</template>
<script>
export default{
    data: function(){
        return{
            username:'',
            password:''
        }
    },
    created:function(){
        this.username = localStorage.getItem('usr')
        this.username = localStorage.getItem('pwd')
    },
    methods: {
        simpan: function(){
            localStorage.setItem('usr',this.username)
            localStorage.setItem('pwd',this.password)
        },
        hapus: function(){
            localStorage.removeItem('usr')
            localStorage.removeItem('pwd')
            this.username = ''
            this.password = ''
        }
    }
}
</script>