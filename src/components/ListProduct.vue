<template>
  <div class="q-pa-md" style="text-align: center;">
    <h1 class="text-h5">List Cake</h1>
    <q-card v-for="(product, index) in products" :key="index" class="q-mb-md">
      <q-card-section class="pink-background">
        <q-item>
          <q-item-section>
            <img :src="product.image" alt="Product" class="product-image" />
          </q-item-section>
          <q-item-section>
            <q-card-title class="product-name">{{ product.name }}</q-card-title>
            <q-card-text>{{ product.description }}</q-card-text>
            <q-card-text class="text-white product-price">{{ product.price }}</q-card-text>
            <q-btn @click="$emit('add-to-cart', product)" color="pink" label="Add to Cart" />
            <q-btn @click="deleteProduct(index)" color="negative" label="Delete" />
          </q-item-section>
        </q-item>
      </q-card-section>
    </q-card>
    <q-btn @click="showAddProductForm = true" color="pink" label="Add Product" />
    
    <!-- Form to add new product -->
    <q-dialog v-model="showAddProductForm">
      <q-card>
        <q-card-section>
          <div class="text-h6">Add New Product</div>
        </q-card-section>
        
        <q-card-section>
          <q-input v-model="newProduct.name" label="Product Name" />
          <q-input v-model="newProduct.price" label="Price" />
          <q-input v-model="newProduct.description" label="Description" />
          <q-input v-model="newProduct.image" label="Image URL" />
        </q-card-section>
        
        <q-card-actions align="right">
          <q-btn flat label="Cancel" v-close-popup />
          <q-btn flat label="Add" color="primary" @click="addProduct" />
        </q-card-actions>
      </q-card>
    </q-dialog>
  </div>
</template>


<script>
export default {
  name: 'ListProduct',
  data() {
    return {
      products: [
        {
          name: 'Chocolate Cupcake',
          price: 'Rp 48.000',
          description: 'Delicious chocolate cake',
          image: 'https://sallysbakingaddiction.com/wp-content/uploads/2017/06/moist-chocolate-cupcakes-5.jpg'
        },
        {
          name: 'Strawberry Cupcake',
          price: 'Rp 50.000',
          description: 'Fresh strawberry cake',
          image: 'https://www.lifeloveandsugar.com/wp-content/uploads/2021/03/Fresh-Strawberry-Cupcakes3.jpg'
        },
        {
          name: 'Matcha CupCake',
          price: 'Rp 45.000',
          description: 'Green tea matcha cake',
          image: 'https://eatwithclarity.com/wp-content/uploads/2022/05/matcha-cupcakes-8.jpg'
        },
        {
          name: 'Orange CupCake',
          price: 'Rp 40.000',
          description: 'Citrus orange cake',
          image: 'https://www.sugarsaltmagic.com/wp-content/uploads/2019/06/Orange-Cupcakes-Recipe-3.jpg'
        },
        {
          name: 'Oreo CupCake',
          price: 'Rp 41.000',
          description: 'Sweet oreo cake',
          image: 'https://sugarspunrun.com/wp-content/uploads/2020/09/Oreo-Cupcakes-1-of-1-9-500x500.jpg'
        },
        {
          name: 'Blueberry CupCake',
          price: 'Rp 46.000',
          description: 'Fresh blueberry cake',
          image: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcStPQBhVpBY58q7jVhlz0hVj8Tj7PMIPNEMiw&s'
        },
        {
          name: 'Vanilla CupCake',
          price: 'Rp 40.000',
          description: 'Creamy vanilla cake',
          image: 'https://natashaskitchen.com/wp-content/uploads/2020/05/Vanilla-Cupcakes-3.jpg'
        },
        {
          name: 'Cheese CupCake',
          price: 'Rp 40.000',
          description: 'Salty cheese cake',
          image: 'https://www.womanscribbles.net/wp-content/uploads/2022/08/cheese-cupcakes-3-735x1103.jpg'
        }
      ],
      showAddProductForm: false,
      newProduct: {
        name: '',
        price: '',
        description: '',
        image: ''
      }
    };
  },
  methods: {
    addProduct() {
      // Validasi input
      if (this.newProduct.name && this.newProduct.price && this.newProduct.description && this.newProduct.image) {
        // Tambahkan produk baru ke daftar
        this.products.push({ ...this.newProduct });
        // Reset form
        this.newProduct = {
          name: '',
          price: '',
          description: '',
          image: ''
        };
        // Tutup dialog
        this.showAddProductForm = false;
      } else {
        // Tampilkan pesan error atau lakukan sesuatu untuk menangani input tidak lengkap
        alert('Please fill in all fields');
      }
    },
    deleteProduct(index) {
      // Logika penghapusan produk
      this.products.splice(index, 1);
    }
  }
};
</script>
<style scoped>
h1 {
  color: rgb(255, 58, 117);
}

.product-image {
  width: 100px;
  height: 100px;
  object-fit: cover;
}

.pink-background {
  background-color: rgb(255, 58, 117);
}

.product-name {
  color: white;
}
</style>
