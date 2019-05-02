<template>
  <q-page class="flex flex-center">
    <img alt="Quasar logo" src="~assets/quasar-logo-full.svg" />

   <q-btn label="Load peoples" @click="loadPeople"/>

   <q-table
    title="Table Title"
    :data="peoples"
    :columns="columns"
    row-key="name"
  />
  </q-page>
</template>

<style></style>

<script>
import axios from "axios";

export default {
  name: "PageIndex",
  methods: {
    loadPeople()  {
        axios.get('https://swapi.co/api/people/')
            .then(res => this.peoples = res.data.results);
    }
  },
  data: () => ({
    peoples: [],
    columns: [
      {
        name: 'desc',
        required: true,
        label: 'Libellé',
        align: 'left',
        field: 'name',
        sortable: true,
        classes: 'my-class',
        style: 'width: 500px'
      }
    ]
  })

};
</script>
