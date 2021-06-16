<template>
  <router-link to="/">Halaman Auth</router-link>
  &nbsp;
  <router-link to="/todo">Halaman Todo</router-link>
  &nbsp;
  <router-link to="/user">Halaman User</router-link>
  <router-view></router-view>
</template>

<script setup>
import Todo from './components/Todo.vue'
import User from './components/User.vue'

// This starter template is using Vue 3 experimental <script setup> SFCs
// Check out https://github.com/vuejs/rfcs/blob/script-setup-2/active-rfcs/0000-script-setup.md
</script>