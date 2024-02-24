<script setup>
    const props = defineProps({
        patient: {
        type:String,
        required:true
        }
    })
</script>

<template>
    <div class="mx-5 my-10 bg-gray-50 border border-gray-300 text-gray-900 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white shadow-md px-5 py-10 rounded-xl">
        <p class="font-bold mb-3  uppercase">ID:
            <span class="font-normal normal-case">
            
            </span>
        </p>

        <p class="font-bold mb-3 uppercase">Nombre:
            <span class="font-normal normal-case">
                 {{patient.name}}
            </span>
        </p>

        <p class="font-bold mb-3 uppercase">Propietario: 
            <span class="font-normal normal-case">
                {{patient.Owner}}
            </span>
        </p>

        <p class="font-bold mb-3 uppercase">Email: 
            <span class="font-normal normal-case">
                {{patient.email}}
            </span>
        </p>

        <p class="font-bold mb-3 uppercase">Fecha Alta:
            <span class="font-normal normal-case">
                {{patient.date}}
            </span>
        </p>

        <p class="font-bold mb-3 uppercase">Síntomas:
            <span class="font-normal normal-case">
                {{patient.symptoms}}
            </span>
        </p>

        <div class="grid md:grid-cols-2 gap-5 mt-10 ">
            <button 
                type="button"
                class="block w-full py-2 px-10 bg-indigo-600 hover:bg-indigo-700 text-white font-bold uppercase rounded-lg"
            >Editar</button>

            <button 
                type="button"
                class="block w-full py-2 px-10 bg-red-600 hover:bg-red-700 text-white font-bold uppercase rounded-lg"
            >Eliminar</button>
        </div>
    </div>
</template>


