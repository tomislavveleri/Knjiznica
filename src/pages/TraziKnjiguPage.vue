<template>
  <q-page padding>
    <!-- Search input field -->
    <q-input
      v-model="searchTerm"
      filled
      type="search"
      hint="Search"
      label="Search for books"
    >
      <template v-slot:append>
        <q-icon name="search" />
      </template>
    </q-input>

    <!-- Filter checkboxes for Author and Title -->
    <div class="q-mt-md">
      <q-checkbox
        v-model="searchByAuthor"
        label="Search by Author"
        color="primary"
        @change="toggleSearchFilter('author')"
      />
      <q-checkbox
        v-model="searchByTitle"
        label="Search by Title"
        color="primary"
        @change="toggleSearchFilter('title')"
      />
    </div>

    <!-- Search button -->
    <q-btn
      color="primary"
      label="Search"
      @click="performSearch"
      class="q-my-md"
    />

    <!-- Component for displaying the filtered book list -->
    <popis-knjiga-page :search-term="searchTerm" :filter-by="activeFilter" />
  </q-page>
</template>

<script>
import { ref } from "vue";
import PopisKnjigaPage from "./PopisKnjigaPage.vue";

export default {
  components: { PopisKnjigaPage },
  setup() {
    // Reactive data for input and filters
    const searchTerm = ref("");
    const searchByAuthor = ref(false);
    const searchByTitle = ref(true); // Default to title search
    const activeFilter = ref("title");

    // Function to perform the search (pass filter choice)
    const performSearch = () => {
      activeFilter.value = searchByAuthor.value ? "author" : "title";
    };

    // Function to toggle between search filters
    const toggleSearchFilter = (filter) => {
      if (filter === "author") {
        searchByTitle.value = false;
        searchByAuthor.value = true;
      } else if (filter === "title") {
        searchByAuthor.value = false;
        searchByTitle.value = true;
      }
    };

    return {
      searchTerm,
      searchByAuthor,
      searchByTitle,
      activeFilter,
      performSearch,
      toggleSearchFilter,
    };
  },
};
</script>
