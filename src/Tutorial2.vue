<script>
export default {
  data(){
    return {
      title:'My New Vue Title',
      message: 'Welcome to Vue',
      titleStatus: {
        red: true,
        fontBig: true,
      },
      input: {
        firstName: '',
        lastName: '',
        isMember: true,
      },
      users: [
      {
        firstName: 'John',
        lastName: 'Smith',
        isMember: false,
      },
      {
        firstName: 'Taro',
        lastName: 'Shinjuku',
        isMember: false,
      },
      {
        firstName: 'Hanako',
        lastName: 'Kouenji',
        isMember: true,
      }
      ],
    }
  },
  methods: {
    addUser() {
      this.users.push(this.input)
      this.input = {
        firstName: '',
        lastName: '',
        isMember: true,
      }
    },
  },
}
</script>

<template>
<h1 :title="message" :class="titleStatus">{{ title }}</h1>
<input type="text" v-model="input.firstName" />
<input type="text" v-model="input.lastName" />
<input type="checkbox" v-model="input.isMember"/>

<button @click="addUser">ADD User!</button>
<h2>ユーザーデータ</h2>
<div v-for="user in users">
  <p>Name: {{ user.firstName + ' ' + user.lastName }}</p>
  <p v-if="user.isMember">メンバーです</p>
  <p v-else>メンバーではありません</p>
</div>
</template>


<style>
.red {
  color: red;
}
.fontBig{
  font-size: 20px;
}
</style>