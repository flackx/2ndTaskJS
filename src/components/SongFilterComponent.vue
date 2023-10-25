<template>
  <div class="songFilter">
    <button @click="applyFilter('None')" :class="{ active: activeFilter === 'None' }">None</button>
    <button @click="applyFilter('Name')" :class="{ active: activeFilter === 'Name' }">Name</button>
    <button @click="applyFilter('Artist')" :class="{ active: activeFilter === 'Artist' }">Artist</button>
  </div>
</template>

<script>
import {ref} from 'vue';

export default {
  name: 'SongFilterComponent',
  props: {
    onFilterChanged: Function,
  },
  setup(props) {

    const activeFilter = ref('None');

    const applyFilter = (filter) => {
      activeFilter.value = filter;
      props.onFilterChanged(filter);
    };

    return {
      activeFilter,
      applyFilter,
    };
  },
};
</script>

<style scoped>

</style>