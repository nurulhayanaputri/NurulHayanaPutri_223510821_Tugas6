<script>
export default {
  name: 'Delete',
  props: {
    modelValue: Boolean // Properti untuk menunjukkan apakah dialog harus dibuka atau tidak
  },
  emits: ['delete', 'cancel'], // Mendefinisikan event yang dapat dipancarkan
  data() {
    return {
      dialogOpen: false // Untuk mengendalikan kapan dialog harus terbuka
    };
  },
  watch: {
    // Mengamati perubahan pada properti modelValue untuk membuka atau menutup dialog
    modelValue(newVal) {
      this.dialogOpen = newVal;
    },
    // Mengamati perubahan pada properti dialogOpen untuk memastikan perubahan dari luar komponen disinkronkan dengan properti modelValue
    dialogOpen(newVal) {
      this.$emit('update:modelValue', newVal);
    }
  },
  methods: {
    // Metode yang dipanggil saat tombol "Hapus" diklik
    confirmDelete() {
      // Tutup dialog setelah tindakan penghapusan selesai
      this.dialogOpen = false;

      // Emit event untuk memberi tahu komponen induk bahwa penghapusan telah dikonfirmasi
      this.$emit('delete');
    },
    // Metode yang dipanggil saat tombol "Batal" diklik
    cancelDelete() {
      // Tutup dialog tanpa melakukan tindakan apa pun
      this.dialogOpen = false;

      // Emit event untuk memberi tahu komponen induk bahwa penghapusan telah dibatalkan
      this.$emit('cancel');
    },
    // Metode yang dipanggil saat dialog ditutup
    onDialogHide() {
      // Mencegah event handling di level induk
      this.$emit('update:modelValue', false);
    }
  }
};
</script>
