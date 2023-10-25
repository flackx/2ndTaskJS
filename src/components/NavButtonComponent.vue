<template>
  <button class="sidebutton" @click="navigateTo" :class="{ active: isActive }">
    <slot></slot>
  </button>
</template>

<script>
export default {
  props: {
    path: String,
    currentPath: String,
  },
  computed: {
    isActive() {
      return this.path === this.currentPath;
    },
  },
  methods: {
    navigateTo() {
      if (this.path !== this.currentPath) {
        this.$router.push(this.path);
      }
    },
  },
};
</script>

<style scoped>

</style>
