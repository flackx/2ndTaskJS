<template>
  <nav id="navigaton" v-if="store.isLoggedIn">
    <ol>
      <li class="meh" v-for="(link, index) in routes" :key="index">
        <router-link :to="link.path">{{ link.name }}</router-link>
      </li>
    </ol>
  </nav>
</template>

<script>
import {store} from '@/store';

export default {
  data() {
    return {
      routes: [
        {
          name: 'Home',
          path: '/home'
        },
        {
          name: 'About me',
          path: '/about-me'
        }
      ],
      store
    }
  },
}
</script>

<style>

</style>