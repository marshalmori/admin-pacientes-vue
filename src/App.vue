<script setup>
import { ref, reactive } from "vue";

import Header from "./components/Header.vue";
import Formulario from "./components/Formulario.vue";

const pacientes = ref([]);

const paciente = reactive({
  nombre: "",
  proprietario: "",
  email: "",
  alta: "",
  sintomas: "",
});

const guardarPaciente = () => {
  pacientes.value.push(paciente);
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
        <div v-if="pacientes.length > 0"></div>
        <p v-else class="text-lg mt-5 text-center mb-10">No Hay pacientes</p>
      </div>
    </div>
  </div>
</template>
