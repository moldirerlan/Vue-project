<template>
    <div v-if="show" class="fixed inset-0 bg-black bg-opacity-50 flex justify-center items-center">
      <div class="bg-white rounded-lg shadow-lg p-6 w-11/12 max-w-md relative">
        <button class="absolute top-2 right-2 text-gray-600 hover:text-gray-900" @click="close">&times;</button>
        <h2 class="text-2xl font-bold mb-4">{{ person.name }}</h2>
        <p class="text-gray-700 mb-2">Email: {{ person.email }}</p>
        <p class="text-gray-700 mb-2">Телефон: {{ person.phone }}</p>
        <p class="text-gray-700 mb-2">Адрес: {{ person.address.street }}, {{ person.address.city }}, {{ person.address.zipcode }}</p>
        <p class="text-gray-700 mb-2">Компания: {{ person.company.name }}</p>
        <p class="text-gray-700">Слоган компании: "{{ person.company.catchPhrase }}"</p>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      show: Boolean,
      person: Object
    },
    methods: {
      close() {
        this.$emit('close');
      }
    }
  }
  </script>
  