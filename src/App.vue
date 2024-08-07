<template>
  <div id="app" class="bg-gray-100 min-h-screen flex flex-col items-center">
    <header class="bg-blue-600 text-white w-full py-4 px-6 shadow-md flex justify-between items-center">
      <h1 class="text-2xl font-bold">Список пользователей</h1>
      <button @click="fetchPeople" class="bg-white text-blue-600 border border-blue-600 py-2 px-4 rounded hover:bg-gray-100">Загрузить пользователей</button>
    </header>
    <div class="card-container flex flex-wrap justify-center gap-6 p-6">
      <PersonCard v-for="person in people" :key="person.id" :person="person" @show-details="showModal" />
    </div>
    <PersonModal v-if="selectedPerson" :show="isModalVisible" :person="selectedPerson" @close="isModalVisible = false" />
  </div>
</template>

<script>
import axios from 'axios';
import PersonCard from './components/PersonCard.vue';
import PersonModal from './components/PersonModal.vue';

export default {
  components: {
    PersonCard,
    PersonModal
  },
  data() {
    return {
      people: [],
      selectedPerson: null,
      isModalVisible: false
    };
  },
  methods: {
    fetchPeople() {
      axios.get('https://jsonplaceholder.typicode.com/users') 
        .then(response => {
          this.people = response.data;
        })
        .catch(error => {
          console.error("Ошибка при загрузке данных о пользователях!", error);
        });
    },
    showModal(person) {
      this.selectedPerson = person;
      this.isModalVisible = true;
    }
  }
}
</script>

<style>
.card-container {
  @apply flex flex-wrap justify-center gap-6 p-6;
}
</style>
