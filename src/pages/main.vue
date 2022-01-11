<template>
  <div class="container">
    <manufacturer v-slot="data">
      <devices :manufacturerId="data.factId" />
    </manufacturer>
  </div>
</template>

<script>
import Manufacturer from '../components/Manufacturer.vue';
import Devices from '../components/Devices.vue';
export default {
  name: 'Main',
  components: {
    Manufacturer: Manufacturer,
    Devices: Devices,
  },
};
</script>
