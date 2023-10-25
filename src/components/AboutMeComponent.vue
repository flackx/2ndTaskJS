<template>
  <div class="aboutMe">
    <h1>ABOUT ME</h1>
    <button @click="toggleFormEditing">{{ editFormButtonLabel }}</button>
    <FormComponent :disabled="isFormDisabled"/>
  </div>
</template>

<script>
import {ref} from 'vue';

export default {
  name: 'AboutMeComponent',
  setup() {
    const isFormEditing = ref(false);

    const toggleFormEditing = () => {
      isFormEditing.value = !isFormEditing.value;
    };

    return {
      isFormEditing,
      toggleFormEditing,
    };
  },
  computed: {
    editFormButtonLabel() {
      return this.isFormEditing ? 'CANCEL' : 'EDIT FORM';
    },
    isFormDisabled() {
      return !this.isFormEditing;
    },
  },
};
</script>

<style scoped>
</style>