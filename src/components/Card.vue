<template>
    <q-drawer v-model="drawerOpen" side="right" bordered>
      <q-card class="pink-background">
        <q-card-section class="row items-center">
          <q-card-title class="text-h6 pink-text">Daftar Pesanan Cake</q-card-title>
          <q-btn flat dense round icon="close" class="self-end" @click="$emit('toggle-cart')" />
        </q-card-section>
        <q-list bordered separator>
          <q-item v-for="(item, index) in cart" :key="index">
            <q-item-section class="pink-text">{{ item.name }}</q-item-section>
            <q-item-section side class="text-right pink-text">{{ item.price }}</q-item-section>
          </q-item>
        </q-list>
      </q-card>
    </q-drawer>
  </template>
  
  <script>
  export default {
    name: 'Cart',
    props: {
      modelValue: Boolean,
      cart: Array
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
  .pink-background {
    background-color: rgb(255, 58, 117); 
  }
  
  .pink-text {
    color: white;
  }
  </style>
  