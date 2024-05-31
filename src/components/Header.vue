<template>
    <q-header elevated class="bg-pink text-white" height-hint="98">
      <q-toolbar>
        <q-btn dense flat round icon="menu" @click="$emit('toggle-left-drawer')" />
        <q-toolbar-title>
          <q-avatar>
            <img src="https://cdn.quasar.dev/logo-v2/svg/logo-mono-white.svg">
          </q-avatar>
          Cake Shop
        </q-toolbar-title>
        <q-space />
        <q-tabs align="right">
          <q-route-tab to="/page1" label="Cake" />
          <q-route-tab to="/page2" label="Drink" />
          <q-route-tab to="/page3" label="Snack" />
        </q-tabs>
        <q-btn dense flat round icon="local_mall" @click="$emit('toggle-cart')" />
      </q-toolbar>
    </q-header>
  </template>
  
  <script>
  export default {
    name: 'Header',
  }
  </script>
  