<script setup>
import { reactive } from "vue";
import Alerta from "./Alerta.vue";

const alerta = reactive({
  tipo: "",
  mensaje: "",
});

const paciente = reactive({
  nombre: "",
  proprietario: "",
  email: "",
  alta: "",
  sintomas: "",
});

const validar = () => {
  if (Object.values(paciente).includes("")) {
    alerta.mensaje = "Todos los campos son obligatorios";
    alerta.tipo = "error";
    return;
  }
};
</script>

<template>
  <div class="md:w-1/2">
    <h2 class="font-black text-3xl text-center mt-10">Seguimiento Pacientes</h2>
    <p class="text-lg mt-5 text-center mb-10">
      Añade Pacientes y
      <span class="text-indigo-600 font-bold">Administralos</span>
    </p>

    <Alerta v-if="alerta.mensaje" :alerta="alerta" />

    <form
      @submit.prevent="validar"
      class="bg-white shadow-md rounded-lg py-10 px-5 mb-10"
    >
      <div class="mb-5">
        <label for="mascota" class="block text-gray-700 uppercase font-bold"
          >Nombre Mascota</label
        >
        <input
          id="mascota"
          type="text"
          placeholder="Nombre de la mascota"
          class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md"
          v-model="paciente.nombre"
        />
      </div>

      <div class="mb-5">
        <label
          for="proprietario"
          class="block text-gray-700 uppercase font-bold"
          >Nombre Proprietario</label
        >
        <input
          id="proprietario"
          type="text"
          placeholder="Nombre del proprietario"
          class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md"
          v-model="paciente.proprietario"
        />
      </div>

      <div class="mb-5">
        <label for="email" class="block text-gray-700 uppercase font-bold"
          >Email</label
        >
        <input
          id="email"
          type="email"
          placeholder="Email del proprietario"
          class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md"
          v-model="paciente.email"
        />
      </div>

      <div class="mb-5">
        <label for="alta" class="block text-gray-700 uppercase font-bold"
          >Alta</label
        >
        <input
          id="alta"
          type="date"
          class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md"
          v-model="paciente.alta"
        />
      </div>

      <div class="mb-5">
        <label for="sintomas" class="block text-gray-700 uppercase font-bold"
          >Síntomas</label
        >
        <input
          id="sintomas"
          placeholder="Describe los síntomas"
          class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md h-40"
          v-model="paciente.sintomas"
        />
      </div>

      <input
        type="submit"
        class="bg-indigo-600 w-full p-3 text-white uppercase font-bold hover:bg-indigo-700 cursor-pointer transition-colors"
        value="Registrar paciente"
      />
    </form>
  </div>
</template>
