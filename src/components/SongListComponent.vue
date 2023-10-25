<template>
  <div class="songList">
    <SongFilterComponent @filterChanged="applyFilter"/>
    <table>
      <thead>
      <tr>
        <th @click="sortName">Name</th>
        <th @click="sortArtist">Artist</th>
      </tr>
      </thead>
      <tbody>
      <tr v-for="song in filteredSongs" :key="song.song">
        <td>{{ song.song }}</td>
        <td>{{ song.artist }}</td>
      </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import {ref, computed, onMounted} from 'vue';
import {store} from '@/store';

export default {
  setup() {
    const songs = ref(store.all_songs);
    const activeFilter = ref('None');
    let originalSongs = [...songs.value];

    onMounted(() => {
      originalSongs = [...songs.value];
    });

    const sortName = () => {
      songs.value.sort((a, b) => a.song.localeCompare(b.song));
      applyFilter('Name');
    };

    const sortArtist = () => {
      songs.value.sort((a, b) => a.artist.localeCompare(b.artist));
      applyFilter('Artist');
    };

    const applyFilter = (filter) => {
      activeFilter.value = filter;

      if (filter === 'None') {
        songs.value = [...originalSongs];
      }
    };

    const filteredSongs = computed(() => {
      if (activeFilter.value === 'Name') {
        return [...songs.value].sort((a, b) => a.song.localeCompare(b.song));
      } else if (activeFilter.value === 'Artist') {
        return [...songs.value].sort((a, b) => a.artist.localeCompare(b.artist));
      } else {
        return [...songs.value];
      }
    });

    return {
      activeFilter,
      sortName,
      sortArtist,
      applyFilter,
      filteredSongs,
    };
  },
};
</script>

<style>
</style>
