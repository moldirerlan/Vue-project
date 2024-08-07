<template>
    <div class="bg-white shadow-lg rounded-lg p-6 w-64 cursor-pointer hover:shadow-xl transition-shadow duration-300" @click="showDetails">
      <h3 class="text-xl font-semibold mb-2">{{ person.name }}</h3>
      <p class="text-gray-600 mb-1">Email: {{ person.email }}</p>
      <p class="text-gray-600">Телефон: {{ person.phone }}</p>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      person: Object
    },
    methods: {
      showDetails() {
        this.$emit('show-details', this.person);
      }
    }
  }
  </script>
  