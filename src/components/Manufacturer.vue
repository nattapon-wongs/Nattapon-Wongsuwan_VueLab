<template>
  <div class="grid grid-cols-2 gap-4 border-black">
    <div class="ml-10 mr-0">
      <h1>Manufacturer</h1>
      <ul v-for="m in manufacturers" :key="m.id" class="border border-black">
        <li>
          <button @click="changeManufacturerId(m.id)">
            <img :src="m.Logo" width="100" />
          </button>
        </li>
      </ul>
    </div>
    <div>
      <slot :factId="currentmanufactID"></slot>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'Manufacturer',
  data() {
    return {
      currentmanufactID: 0,
      manufacturers: [
        { id: 1, Title: 'Asus' },
        { id: 2, Title: 'Dell' },
      ],
    };
  },
  created() {
    this.getManufacturer();
  },
  methods: {
    async getManufacturer() {
      const res = await axios.get('https://demo.yume-dev.me/manufacturers');
      // console.log('Manufacturer', res.data);
      this.manufacturers = res.data;
    },
    changeManufacturerId(id) {
      // console.log('changeManufacturerId ::: ', id);
      this.currentmanufactID = id;
    },
  },
};
</script>
