<script setup></script>

<template>
  <div class="md:w-1/2 text-black dark:text-white">
    <h2 class="font-black text-3xl text-center">Seguimiento Pacientes</h2>
    <p class="text-lg mt-5 text-center mb-10">
      Añade pacientes y
      <span class="text-indigo-600 font-bold">Adminístralos</span>
    </p>
    <form>
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
          required
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
          required
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
          required
        />
      </div>
      <div class="mb-6">
        <label
          for="release_date"
          class="block mb-2 text-sm font-medium text-gray-900 dark:text-white"
          >Alta</label
        >
        <div class="relative max-w-sm">
          <div class="absolute inset-y-0 start-0 flex items-center ps-3 pointer-events-none">
            <svg class="w-4 h-4 text-gray-500 dark:text-gray-400" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="currentColor" viewBox="0 0 20 20">
                <path d="M20 4a2 2 0 0 0-2-2h-2V1a1 1 0 0 0-2 0v1h-3V1a1 1 0 0 0-2 0v1H6V1a1 1 0 0 0-2 0v1H2a2 2 0 0 0-2 2v2h20V4ZM0 18a2 2 0 0 0 2 2h16a2 2 0 0 0 2-2V8H0v10Zm5-8h10a1 1 0 0 1 0 2H5a1 1 0 0 1 0-2Z"/>
              </svg>
          </div>
          <input  id="release_date" 
                  datepicker 
                  datepicker-autohide 
                  datepicker-format="dd/mm/yyyy"
                  type="text"
                  class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full ps-10 p-2.5  dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" 
                  placeholder="Select date"
          >
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
          required
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
