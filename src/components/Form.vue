<script setup>
  import { reactive } from 'vue'
  import Alert from './Alert.vue'

  const alert = reactive ({
    type:'',
    message:''
  })

  const emit = defineEmits([
    'update:name',
    'update:owner',
    'update:email',
    'update:date',
    'update:symptoms',
    'save-patient'
  ])

  const props = defineProps({
    name: {
      type:String,
      required:true
    },
    owner: {
      type:String,
      required:true
    },
    email: {
      type:String,
      required:true
    },
    date: {
      type:String,
      required:true
    },
    symptoms: {
      type:String,
      required:true
    },
  })

  const validateForm = () => {
    if(Object.values(props).includes('')){
      alert.message = 'Todos los campos son obligatorios'
      alert.type = 'error'
      return
    }
    emit('save-patient')
  }

</script>

<template>
  <div class="md:w-1/2 text-black dark:text-white">
    <h2 class="font-black text-3xl text-center">Seguimiento Pacientes</h2>
    <p class="text-lg mt-5 text-center mb-10">
      Añade pacientes y
      <span class="text-indigo-600 font-bold">Adminístralos</span>
    </p>
    <Alert 
      v-if="alert.message"
      :alert = "alert"
    />
    <form @submit.prevent="validateForm">
      <div class="mb-6">
        <label
          for="pet_name"
          class="block mb-2 text-sm font-medium text-gray-900 dark:text-white"
          >Nombre mascota</label
        >
        <input
          type="text"
          id="pet_name"
          class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
          placeholder="Nombre de la mascota"
          :value="name"
          @input="$emit('update:name', $event.target.value)"
        />
      </div>
      <div class="mb-6">
        <label
          for="owner_name"
          class="block mb-2 text-sm font-medium text-gray-900 dark:text-white"
          >Nombre Propietario</label
        >
        <input
          type="text"
          id="owner_name"
          class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
          placeholder="Nombre del propietario"
          :value="owner"
          @input="$emit('update:owner', $event.target.value)"
        />
      </div>
      <div class="mb-6">
        <label
          for="email"
          class="block mb-2 text-sm font-medium text-gray-900 dark:text-white"
          >Email</label
        >
        <input
          type="email"
          id="email"
          class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
          placeholder="juan123@yopmail.com"
          :value="email"
          @input="$emit('update:email', $event.target.value)"
        />
      </div>
      <div class="mb-6">
        <label
          for="release_date"
          class="block mb-2 text-sm font-medium text-gray-900 dark:text-white"
          >Alta</label
        >
        <div class="relative max-w-sm">
          <input
            type="date"
            id="release_date"
            class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
            placeholder=""
            :value="date"
            @input="$emit('update:date', $event.target.value)"
          />
        </div>
      </div>
      <div class="mb-6">
        <label
          for="symptoms"
          class="block mb-2 text-sm font-medium text-gray-900 dark:text-white"
          >Síntomas</label
        >
        <textarea
          type="text"
          id="symptoms"
          class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500 h-40"
          placeholder="Describe los sintomas"
          :value="symptoms"
          @input="$emit('update:symptoms', $event.target.value)"
        />
      </div>
      <button
        type="submit"
        class="text-white bg-indigo-600 hover:bg-indigo-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm w-full px-5 py-2.5 text-center dark:bg-indigo-600 dark:hover:bg-indigo-800 dark:focus:ring-blue-800"
      >
        Registrar Paciente
      </button>
    </form>
  </div>
</template>
