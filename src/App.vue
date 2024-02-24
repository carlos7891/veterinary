<script setup>
  import Header from './components/Header.vue'
  import Form from './components/Form.vue'
  import Patient from './components/Patient.vue'
  import { ref, reactive } from 'vue'

  const patients = ref ([])

  const patient = reactive({
    name:'',
    owner:'',
    email:'',
    date:'',
    symptoms:''
  })

  const savePatient = () => {
    patients.value.push({...patient})
    Object.assign(patient, {
      name:'',
      owner:'',
      email:'',
      date:'',
      symptoms:''
    })
  }

</script>

<template>
  <div class="container mx-auto mt-20">
    <Header/>
    <div class="mt-12 md:flex">
      <Form
        v-model:name = "patient.name"
        v-model:owner = "patient.owner"
        v-model:email = "patient.email"
        v-model:date = "patient.date"
        v-model:symptoms = "patient.symptoms"
        @save-patient = "savePatient"
      />
      <div class="md:w-1/2 md:h-screen ml-2">
        <h3 class="font-black text-black dark:text-white text-3xl text-center">
          Administra tus pacientes
        </h3>
        <p class="text-lg mt-5 text-center mb-10 text-black dark:text-white">
          Informacion de
          <span class="text-indigo-600 font-bold">Pacientes</span>
        </p>
        <div v-if="patients.length > 0">
          <Patient
            v-for="patient in patients"
            :patient="patient"
          />
        </div>
        <p v-else class="mt-10 text-2xl text-black dark:text-white">No hay pacientes</p>
      </div>
    </div>
  </div>
</template>
