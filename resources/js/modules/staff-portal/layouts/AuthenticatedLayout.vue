<script setup>
import { defineComponent, onMounted, ref, watch } from "vue";
import { router, usePage } from "@inertiajs/vue3";
import { useQuasar } from "quasar";

defineComponent({
  name: "AuthenticatedLayout",
});

const LEFT_DRAWER_STORAGE_KEY = "advanta-report.layout.left-drawer-open";
const $q = useQuasar();
const page = usePage();
const leftDrawerOpen = ref(
  JSON.parse(localStorage.getItem(LEFT_DRAWER_STORAGE_KEY))
);
const isDropdownOpen = ref(false);
const toggleLeftDrawer = () => (leftDrawerOpen.value = !leftDrawerOpen.value);

watch(leftDrawerOpen, (newValue) => {
  localStorage.setItem(LEFT_DRAWER_STORAGE_KEY, newValue);
});

onMounted(() => {
  leftDrawerOpen.value = JSON.parse(
    localStorage.getItem(LEFT_DRAWER_STORAGE_KEY)
  );

  if ($q.screen.lt.md) {
    leftDrawerOpen.value = false;
  }
});
</script>

<template>
  <q-layout view="lHh LpR lFf">
    <q-header bordered class="bg-grey-1 text-dark q-py-sm q-px-xl">
      <q-toolbar class="q-pa-none">
        <div class="flex items-center q-gutter-x-md">
          <q-avatar color="grey-3" size="60px"><img src="../assets/img/favicon.png" alt=""> </q-avatar>
          <q-toolbar-title
          :class="{ 'q-ml-sm': leftDrawerOpen}"
          class="text-h6 text-weight-bold">
        <slot name="title">{{ $config.APP_NAME }}</slot></q-toolbar-title>
        </div>
        <q-space />
        <div
          class="flex items-center q-gutter-x-sm bg-grey-2 q-pa-sm"
          style="border-radius: 15px"
        >
          <q-avatar size="50px">
            <img
              src="https://cdn.quasar.dev/img/boy-avatar.png"
              alt="Foto Profil Pengguna"
            />
          </q-avatar>

          <span class="text-subtitle1 text-weight-bold">Jhon Example</span>

          <q-btn flat round dense icon="more_vert" text-color="grey-7" />
        </div>
      </q-toolbar>
    </q-header>

    <q-page-container class="bg-grey-1">
      <q-page class="q-px-xl q-py-lg">
        <slot></slot>
      </q-page>
    </q-page-container>
    <slot name="footer"></slot>
  </q-layout>
</template>

<style>
.profile-btn span.block {
  text-align: left !important;
  width: 100% !important;
  margin-left: 10px !important;
}
</style>
<style scoped>
.q-toolbar {
  border-bottom: 1px solid transparent;
  /* Optional border line */
}

.toolbar-scrolled {
  box-shadow: 0px 1px 2px rgba(0, 0, 0, 0.05);
  /* Add shadow */
  border-bottom: 1px solid #ddd;
  /* Optional border line */
}

.profile-btn-active {
  background-color: #ddd !important;
}

#profile-btn-popup .q-item--active {
  color: inherit !important;
}
</style>
