<template>
  <div class="parent-component">
    <h1>SELAMAT DATANG :)</h1>
    <!-- Memanggil ChildComponent dan menangkap event childEvent -->
    <ChildComponent @childEvent="handleChildEvent">
      <!-- Slot untuk menyisipkan konten tambahan -->
      <template #additionalContent>
        <p>TERIMA KASIH TELAH BERBELANJA</p>
      </template>
    </ChildComponent>
    <div v-if="childData.length > 0">
      <p>Data yang diterima dari ChildComponent:</p>
      <ul class="child-data-list">
        <li v-for="(data, index) in childData" :key="index" class="child-data-item">{{ data }}</li>
      </ul>
    </div>
    <div v-else>
      <p>Tidak ada data dari ChildComponent</p>
    </div>
  </div>
</template>

<script>
import ChildComponent from './ChildComponent.vue';

export default {
  components: {
    ChildComponent
  },
  data() {
    return {
      childData: []
    };
  },
  methods: {
    handleChildEvent(data) {
      // Tangani event dari ChildComponent
      this.childData.push(data);
    }
  }
};
</script>

<style scoped>
.parent-component {
  background-color: #f0f5f9; /* Warna biru muda */
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1); /* Bayangan lembut */
}

.parent-component h1 {
  color: #333; /* Warna teks hitam */
  margin-bottom: 20px; /* Ruang bawah antara judul dan konten */
}

.parent-component p {
  color: #666; /* Warna teks abu-abu */
}

.child-data-list {
  list-style-type: none; /* Hilangkan bullet */
  padding-left: 0; /* Hilangkan padding kiri */
}

.child-data-item {
  background-color: #fff; /* Warna latar belakang putih */
  padding: 10px;
  border-radius: 4px;
  margin-bottom: 5px; /* Ruang antara setiap item */
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1); /* Bayangan lembut */
}

/* Styling untuk tombol Submit */
.submit-button {
  background-color: #3498db; /* Warna biru */
  color: #fff; /* Warna teks putih */
  padding: 10px 20px; /* Padding */
  border: none; /* Hapus border */
  border-radius: 4px; /* Tambahkan sudut bulat */
  cursor: pointer; /* Ubah kursor saat hover */
  transition: background-color 0.3s ease; /* Transisi halus saat hover */
}

.submit-button:hover {
  background-color: #2980b9; /* Warna biru muda saat hover */
}
</style>
