<template>
  <q-layout view="hHh lpR fFf">
    <Header @toggle-left-drawer="toggleLeftDrawer" @toggle-cart="toggleCart" />

    <Drawer v-model="leftDrawerOpen" />

    <Cart v-model="cartOpen" :cart="cart" @toggle-cart="toggleCart" />

    <q-page-container>
      <ProductList :products="products" @add-to-cart="addToCart" @open-delete-dialog="openDeleteDialog" />
    </q-page-container>

    <!-- Menggunakan komponen Delete dan mengontrolnya dengan variabel deleteDialogOpen -->
    <Delete v-model="deleteDialogOpen" @delete="deleteItem" @cancel="cancelDelete" />

    <q-footer elevated class="bg-pink text-white" style="text-align: center;">
      <q-toolbar>
        <q-toolbar-title>
          <q-avatar>
            <img src="https://cdn.quasar.dev/logo-v2/svg/logo-mono-white.svg">
          </q-avatar>
          <div>&copy;2024 Nurul Hayana Putri </div>
        </q-toolbar-title>
      </q-toolbar>
    </q-footer>
  </q-layout>
</template>

<script>
import { ref } from 'vue'
import Header from './components/Header.vue'
import Drawer from './components/Sidebar.vue'
import Cart from './components/Card.vue'
import ProductList from './components/ListProduct.vue'
import Delete from './components/Delete.vue'

export default {
  name: 'App',
  components: {
    Header,
    Drawer,
    Cart,
    ProductList,
    Delete
  },
  setup() {
    const leftDrawerOpen = ref(false)
    const cartOpen = ref(false)
    const cart = ref([])
    const products = ref([])

    const deleteDialogOpen = ref(false)
    const deleteIndex = ref(null)

    const toggleLeftDrawer = () => {
      leftDrawerOpen.value = !leftDrawerOpen.value
    }

    const toggleCart = () => {
      cartOpen.value = !cartOpen.value
    }

    const addToCart = (product) => {
      cart.value.push(product)
    }

    // Fungsi untuk membuka dialog konfirmasi penghapusan
    const openDeleteDialog = (index) => {
      deleteIndex.value = index
      deleteDialogOpen.value = true
    }

    const deleteItem = () => {
      if (deleteIndex.value !== null && deleteIndex.value >= 0 && deleteIndex.value < products.value.length) {
        products.value.splice(deleteIndex.value, 1)
        deleteIndex.value = null
        deleteDialogOpen.value = false
      } else {
        console.error('Invalid delete index or index out of range')
      }
    }

    const cancelDelete = () => {
      deleteIndex.value = null
      deleteDialogOpen.value = false
    }


    return {
      leftDrawerOpen,
      cartOpen,
      cart,
      products,
      deleteDialogOpen,
      toggleLeftDrawer,
      toggleCart,
      addToCart,
      openDeleteDialog,
      deleteItem,
      cancelDelete
    }
    return {
      products,
      deleteDialogOpen,
      openDeleteDialog,
      deleteItem,
      cancelDelete
    }
  }
}
</script>
