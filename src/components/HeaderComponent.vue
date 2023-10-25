<template>
  <div class="header">
    <div class="gggamebrotherincrhist">
      <img src="@/assets/logo%20(white).svg" alt="logo" class="logo"/>
      <span class="logo-text">I was crazy once</span>
    </div>
      <div v-if="store.isLoggedIn" class="user">
        <span class="avatar"></span>
        <h3>{{ fullName }}</h3>
    </div>
    <button class="stupidbutton" @click="store.loginManager()">{{ store.isLoggedIn ? 'LOGOUT' : 'LOGIN' }}</button>
  </div>
</template>

<script>
import {store} from '@/store';

export default {

  data() {
    return {
      store
    }
  },
  computed: {
    fullName() {
      return `${store.user.name} ${store.user.surname}`;
    }
  }
}
</script>

<style>

</style>

