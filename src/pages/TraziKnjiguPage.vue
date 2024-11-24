<template>
  <q-page padding>
    <q-input v-model="searchKnjiga" filled type="search" hint="Search">
      <template v-slot:append>
        <q-icon name="search" />
      </template>
    </q-input>

    <q-btn color="primary" label="Primary" @click="searchKnjiga" />

    <popis-knjiga-page />
  </q-page>
</template>

<script>
import PopisKnjigaPage from "./PopisKnjigaPage.vue";

export default {
  components: { PopisKnjigaPage },
  // name: 'PageName',
  setup() {},
};
</script>
