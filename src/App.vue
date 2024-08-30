<script setup>
  import { ref, reactive, watch, onMounted } from 'vue'
  import { uid } from 'uid'
  import Header from './components/Header.vue'
  import Form from './components/Form.vue'
  import Patient from './components/Patient.vue'

  const patients = ref ([])

  const patient = reactive({
    id: null,
    name:'',
    owner:'',
    email:'',
    date:'',
    symptoms:''
  })

  watch(patients, () => {
    saveLocalStorage()
  }, {
    deep:true
  }) 

  onMounted(() => {
    const patientsStorage = localStorage.getItem('patients')
    if(patientsStorage){
      patients.value = JSON.parse(patientsStorage)
    }
  })

  const savePatient = () => {
    if(patient.id) {
      const { id } = patient
      const i = patients.value.findIndex((patient) => patient.id === id )
      patients.value[i] = { ...patient}
    } else {
      patients.value.push({ ...patient, id: uid() })
    }
    Object.assign(patient, {
      id: null,
      name:'',
      owner:'',
      email:'',
      date:'',
      symptoms:''
    })
  }

  const updatePatient = (id) => {
    const editPatient = patients.value.filter(patient => patient.id === id)[0]
    Object.assign(patient, editPatient)
  }

  const deletePatient = (id) => {
    patients.value = patients.value.filter(patient => patient.id !== id)
  }

  const saveLocalStorage = () => {
    localStorage.setItem('patients', JSON.stringify(patients.value))
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
        :id="patient.id"
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
            @update-patient = "updatePatient"
            @delete-patient = "deletePatient"
          />
        </div>
        <p v-else class="mt-10 text-2xl text-black dark:text-white">No hay pacientes</p>
      </div>
    </div>
  </div>
</template>
