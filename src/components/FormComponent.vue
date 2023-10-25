<template>
  <div class="formComponent">
    <form>
      <div class="form-group">
        <label for="firstName">First name</label>
        <input type="text" id="firstName" v-model="user.name" :disabled="disabled" class="custom-input"/>
      </div>
      <div class="form-group">
        <label for="lastName">Last name</label>
        <input type="text" id="lastName" v-model="user.surname" :disabled="disabled" class="custom-input"/>
      </div>
      <div class="form-group">
        <label for="studentCode">Student code</label>
        <input type="text" id="studentCode" v-model="user.code" :disabled="disabled" class="custom-input"/>
      </div>
    </form>
  </div>
</template>

<script>
import {ref} from 'vue';
import {store} from '@/store';

export default {
  props: {
    disabled: Boolean,
  },
  setup() {
    const user = ref(store.user);

    return {
      user,
    };
  },
};
</script>
<style scoped>
.formComponent {
  text-align: left;
  margin-left: 20px;
}

.form-group {
  margin-bottom: 10px;
}

label {
  font-weight: bold;
  color: Rebeccapurple;
  background: transparent;
}

.custom-input {
  width: 100%;
  padding: 5px;
  background: transparent; /* Remove the background (set to transparent) */
  border: 1px solid rebeccapurple; /* Add a border for separation */
  color: white; /* Change text color */
}

input:focus {
  outline: none; /* Remove the focus border */
  border: 1px solid #45e8a4; /* Change border color when input is focused */
}
</style>