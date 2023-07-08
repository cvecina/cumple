<template>
  <!-- <div class="min-h-screen flex relative lg:static surface-ground background">
    <div
      id="app-sidebar-1"
      class="surface-section h-screen hidden lg:block flex-shrink-0 absolute lg:static left-0 top-0 z-1 border-right-1 surface-border select-none background"
      style="width: 280px"
    >
      <div class="flex flex-column h-full">
        <ul class="list-none p-3 m-0">
          <li>
            <ul
              class="list-none p-0 m-0 overflow-hidden"
              v-for="list in listSideBar"
              :key="list"
            >
              <li>
                <a
                  v-ripple
                  class="flex align-items-center cursor-pointer p-3 border-round text-700 hover:surface-100 transition-duration-150 transition-colors p-ripple"
                  @click="list.command()"
                >
                  <i :class="list.icon + ' mr-2'"></i>
                  <span class="font-medium">{{ list.label }}</span>
                </a>
              </li>
            </ul>
          </li>
        </ul>
      </div>
    </div>
    <div class="min-h-screen flex flex-column relative flex-auto">
      <div
        class="flex justify-content-between align-items-center px-5 surface-0 border-bottom-1 surface-border relative lg:static"
      >
        <div class="flex">
          <a
            v-ripple
            class="cursor-pointer block lg:hidden text-700 mr-3 mt-1 p-ripple"
            v-styleclass="{
              selector: '#app-sidebar-1',
              enterClass: 'hidden',
              enterActiveClass: 'fadeinleft',
              leaveToClass: 'hidden',
              leaveActiveClass: 'fadeoutleft',
              hideOnOutsideClick: true,
            }"
          >
            <i class="pi pi-bars text-4xl"></i>
          </a>
        </div>
      </div> -->
      <!-- <div class="p-1 flex flex-column flex-auto"> -->
          <!-- AQUI VA EL CONTENIDO -->
          <div class="surface-ground px-4 py-5 md:px-6 lg:px-8">
            <div
              class="surface-card shadow-2 border-round flex p-3 flex-column md:flex-row"
            >
              <!-- Loop through the menu items -->
              <template v-for="item in menuItems" :key="item">
                <div
                  :class="[
                    'border-bottom-1',
                    item.borderClass,
                    'surface-border',
                    'flex-auto',
                    'p-3',
                  ]"
                >
                  <div class="flex align-items-center mb-3">
                    <i :class="item.iconClass"></i>
                    <span class="text-500 font-medium">{{ item.title }}</span>
                  </div>
                  <span class="block text-900 font-medium mb-4 text-xl">{{
                    item.value
                  }}</span>
                  <div class="flex align-items-center">
                    <i :class="item.changeIconClass"></i>
                    <span :class="item.changeValueClass">{{
                      item.changeValue
                    }}</span>
                  </div>
                </div>
              </template>
            </div>
          </div>
          <DataTableRepository :showCreate="false" title="Tickets recientes" :camposTabla="camposTabla" :data="dataDataTable"></DataTableRepository>
          <!-- HASTA AQUÍ -->
        <!-- </div> -->
      <!-- </div> -->
    <!-- </div> -->
</template>
  
  <script setup>
import { ref, computed } from "vue";
import { useRouter } from "vue-router";
import { useI18n } from "vue-i18n";
import { DataTableRepository } from "@/componentsFromRepository";
const { t } = useI18n();
const router = useRouter();

const GestionarSoluciones = computed(() => t("Gestionar soluciones"));

const mostrarGestionSoluciones = () => {
  router.push("/dashboardadmin");
};

const mostrarGestionarImportes = () => {
  router.push("/dashboardadmin");
};

const mostrarGestionarRequisitos = () => {
  router.push("/dashboardadmin");
};

const mostrarGestionarRecursos = () => {
  router.push("/dashboardadmin");
};

const mostrarGestionarImagenes = () => {
  router.push("/dashboardadmin");
};
const listSideBar = ref([
  {
    label: GestionarSoluciones,
    icon: "pi pi-briefcase",
    command: mostrarGestionSoluciones,
  },
  {
    label: "Gestionar importes",
    icon: "pi pi-money-bill",
    command: mostrarGestionarImportes,
  },
  {
    label: "Gestionar requisitos",
    icon: "pi pi-file",
    command: mostrarGestionarRequisitos,
  },
  {
    label: "Gestionar recursos",
    icon: "pi pi-user",
    command: mostrarGestionarRecursos,
  },
  {
    label: "Gestionar imágenes",
    icon: "pi pi-image",
    command: mostrarGestionarImagenes,
  },
]);

const camposTabla = ref([
    { campo: "barco", label: "Barco" },
    { campo: "fecha", label: "Fecha" },
    { campo: "importe", label: "Importe" },
    { campo: "estado", label: "Estado" },
    {campo: "cliente", label: "Cliente"},
])

const dataDataTable = ref([
    {barco: "Barco 1", fecha: "01/01/2021", importe: "1000€", estado: "Pendiente", cliente: "Cliente 1"},
    {barco: "Barco 2", fecha: "02/01/2021", importe: "2000€", estado: "Pendiente", cliente: "Cliente 2"},
    {barco: "Barco 3", fecha: "03/01/2021", importe: "3000€", estado: "Pendiente", cliente: "Cliente 3"},
    {barco: "Barco 4", fecha: "04/01/2021", importe: "4000€", estado: "Pendiente", cliente: "Cliente 4"},
    {barco: "Barco 5", fecha: "05/01/2021", importe: "5000€", estado: "Completado", cliente: "Cliente 5"},
])

const menuItems = ref([
  {
    title: "Barcos",
    iconClass: "pi pi-shopping-cart text-blue-500 text-xl mr-2",
    value: "10",
    // changeIconClass: "pi pi-arrow-down text-pink-500 text-xl mr-2",
    // changeValueClass: "text-pink-500 font-medium",
    // changeValue: "2",
    borderClass: "md:border-right-1 md:border-bottom-none",
  },
  {
    title: "Ingresos totales",
    iconClass: "pi pi-shopping-cart text-orange-500 text-xl mr-2",
    value: "2000€",
    changeIconClass: "pi pi-arrow-up text-green-500 text-xl mr-2",
    changeValueClass: "text-green-500 font-medium",
    changeValue: "+15",
    borderClass: "md:border-right-1 md:border-bottom-none",
  },
  {
    title: "Clientes",
    iconClass: "pi pi-users text-cyan-500 text-xl mr-2",
    value: "12",
    changeIconClass: "pi pi-arrow-up text-green-500 text-xl mr-2",
    changeValueClass: "text-green-500 font-medium",
    changeValue: "+12%",
    borderClass: "md:border-right-1 md:border-bottom-none",
  },
  {
    title: "Comentarios",
    iconClass: "pi pi-users text-purple-500 text-xl mr-2",
    value: "7",
    changeIconClass: "pi pi-arrow-up text-green-500 text-xl mr-2",
    changeValueClass: "text-green-500 font-medium",
    changeValue: "+20",
    borderClass: "md:border-right-1 md:border-bottom-none",

  },
]);
</script>
  
  <style>
</style>