<template>
  <div id="app">
    <!-- Komponen Induk -->
    <ParentComponent>
      <!-- Slot untuk menerima data dari ChildComponent -->
      <template v-slot:receivedData="data">
        <p>Data dari Komponen Anak: {{ data }}</p>
      </template>
      <!-- Komponen Anak -->
      <ChildComponent @childEvent="handleChildEvent" />
    </ParentComponent>
  </div>
</template>

<script>
import ParentComponent from './components/ParentComponent.vue';
import ChildComponent from './components/ChildComponent.vue';

export default {
  components: {
    ParentComponent,
    ChildComponent
  },
  methods: {
    handleChildEvent(data) {
      // Menangani event dari ChildComponent
      console.log('Data dari Komponen Anak:', data);
    }
  }
};
</script>


