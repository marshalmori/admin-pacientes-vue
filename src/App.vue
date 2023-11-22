<script setup>
import { ref, reactive } from "vue";

import Header from "./components/Header.vue";
import Formulario from "./components/Formulario.vue";
import Paciente from "./components/Paciente.vue";

const pacientes = ref([]);

const paciente = reactive({
  nombre: "",
  proprietario: "",
  email: "",
  alta: "",
  sintomas: "",
});

const guardarPaciente = () => {
  pacientes.value.push({ ...paciente });

  //Reiniciar el objeto
  Object.assign(paciente, {
    nombre: "",
    proprietario: "",
    email: "",
    alta: "",
    sintomas: "",
  });
};
</script>

<template>
  <div class="container mx-auto mt-20">
    <Header />

    <div class="'mt-12 md:flex md:flex-row">
      <Formulario
        v-model:nombre="paciente.nombre"
        v-model:proprietario="paciente.proprietario"
        v-model:email="paciente.email"
        v-model:alta="paciente.alta"
        v-model:sintomas="paciente.sintomas"
        @guardar-paciente="guardarPaciente"
      />

      <div class="md:w-1/2 md:h-screen overflow-y-scroll mt-10">
        <h3 class="font-black text-3xl text-center">
          Administra tus Pacientes
        </h3>
        <p class="text-lg mt-5 text-center mb-10">
          Información de
          <span class="text-indigo-600 font-bold">Pacientes</span>
        </p>

        <div v-if="pacientes.length > 0">
          <Paciente v-for="paciente in pacientes" :paciente="paciente" />
        </div>
        <p v-else class="text-lg mt-5 text-center mb-10">No Hay pacientes</p>
      </div>
    </div>
  </div>
</template>
