<template>
    <q-drawer v-model="drawerOpen" show-if-above side="left" bordered>
      <q-toolbar>
        <q-toolbar-title class="pink-text">List Cake</q-toolbar-title>
      </q-toolbar>
      <q-list class="pink-text">
        <q-item v-for="(cake, index) in cakes" :key="index" clickable v-ripple>
          <q-item-section>{{ cake }}</q-item-section>
        </q-item>
      </q-list>
    </q-drawer>
  </template>
  
  <script>
  export default {
    name: 'Drawer',
    props: {
      modelValue: Boolean
    },
    data() {
      return {
        cakes: [
          'Chocolate Cupcake',
          'Vanilla Cupcake',
          'Red Velvet Cupcake',
          'Lemon Cupcake',
          'Cheese Cupcake',
          'Blueberry Cupcake',
          'Rasberry Cupcake',
          'Carrot Cupcake'
        ]
      }
    },
    computed: {
      drawerOpen: {
        get() {
          return this.modelValue
        },
        set(val) {
          this.$emit('update:modelValue', val)
        }
      }
    }
  }
  </script>
  
  <style scoped>
  .q-toolbar {
    background-color: white;
  }
  
  .pink-text {
    color: rgb(255, 58, 117);
  }
  </style>
  