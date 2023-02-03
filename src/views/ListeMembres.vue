<script setup>
import { ref, onMounted, inject } from 'vue';
import { useMembresStore } from '@/stores/membres'

const membresStore = useMembresStore();


</script>

<template>
  <main>
    <h2 class="title">Liste des membres</h2>
    <ul class="columns is-gap">
      <li class="column is-12-mobile is-6-tablet is-4-desktop box" v-for="membre in membresStore.state.membres">
        <router-link :to="{ name: 'profil-membre', params: { id: membre.id } }">
          <img src="https://cdn-icons-png.flaticon.com/512/6716/6716646.png" alt="" width="64" height="64">
          <h2 class="title is-3">{{ membre.fullname }}</h2>
          <p class="subtitle">{{ membre.email }}</p>
        </router-link>
      </li>
    </ul>
  </main>
</template>
<style scoped>

ul{
  flex-wrap: wrap;
}
li:last-of-type{
  margin-bottom: 1.5rem;
}
img{
  float: left;
  margin-right: 1em;
}

.box {
  transition: background-color .3s ease-in-out;
}

.box:hover {
  background-color: rgba(32, 156, 238, 0.3);
}

</style>
