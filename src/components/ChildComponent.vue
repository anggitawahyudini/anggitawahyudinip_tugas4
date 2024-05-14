<template>
  <div class="child-component">
    <h2>BILL BELANJA</h2>
    <!-- Menampilkan konten tambahan yang dimasukkan dari ParentComponent -->
    <slot name="additionalContent"></slot>
    <!-- Form untuk memasukkan data -->
    <form @submit.prevent="submitForm" class="form">
      <div class="form-group">
        <label for="inputData">Nama:</label>
        <input type="text" id="inputData" v-model="inputData" class="input-field">
      </div>
      <div class="form-group">
        <label for="inputAddress">Alamat:</label>
        <input type="text" id="inputAddress" v-model="inputAddress" class="input-field">
      </div>
      <div class="form-group">
        <label for="inputPhoneNumber">Nomor Telepon:</label>
        <input type="text" id="inputPhoneNumber" v-model="inputPhoneNumber" class="input-field">
      </div>
      <div class="form-group">
        <label for="inputOption">Pilihan:</label>
        <select id="inputOption" v-model="selectedOption" class="input-field">
          <option value="Member">Member</option>
          <option value="Non-Member">Non-Member</option>
        </select>
      </div>
      <button type="submit" class="submit-button">Submit</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      inputData: '',
      inputAddress: '',
      inputPhoneNumber: '',
      selectedOption: 'Member' // Default: 'Member'
    };
  },
  methods: {
    // Memanggil event submitForm saat form disubmit
    submitForm() {
      // Menggabungkan data yang dimasukkan
      const data = {
        inputData: this.inputData,
        inputAddress: this.inputAddress,
        inputPhoneNumber: this.inputPhoneNumber,
        selectedOption: this.selectedOption
      };
      
      // Emit event childEvent dengan data yang dimasukkan
      this.$emit('childEvent', data);
      // Reset form setelah disubmit
      this.inputData = '';
      this.inputAddress = '';
      this.inputPhoneNumber = '';
      this.selectedOption = 'Member'; // Reset pilihan ke 'Member'
    }
  }
};
</script>

<style scoped>
.child-component {
  background-color: #eaf2f8; /* Warna biru muda */
  padding: 15px;
  margin-bottom: 15px;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1); /* Bayangan lembut */
}

.child-component h2 {
  color: #333; /* Warna teks hitam */
}

.form {
  margin-top: 10px; /* Ruang atas dari form */
}

.form-group {
  margin-bottom: 15px; /* Ruang bawah antara grup form */
}

.input-field {
  width: 100%; /* Lebar input 100% */
  padding: 8px; /* Padding */
  border-radius: 4px; /* Tambahkan sudut bulat */
  border: 1px solid #ccc; /* Tambahkan border */
}

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
