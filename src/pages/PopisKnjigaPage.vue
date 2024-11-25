<template>
  <q-page>
    <!-- Table for displaying filtered books -->
    <q-table :rows="filteredBooks" :columns="columns" row-key="id">
      <template v-slot:body-cell-image="props">
        <!-- Display book image if available -->
        <q-img
          :src="props.row.image"
          alt="Book Image"
          style="width: 50px; height: 50px"
        />
      </template>
      <template v-slot:body-cell-available="props">
        <!-- Display availability as Yes/No -->
        <q-chip :color="props.row.available ? 'green' : 'red'" outline>
          {{ props.row.available ? "Yes" : "No" }}
        </q-chip>
      </template>
    </q-table>
  </q-page>
</template>

<script>
import { computed, ref, watch } from "vue";

export default {
  props: {
    searchTerm: {
      type: String,
      default: "",
    },
    filterBy: {
      type: String,
      default: "title", // Can be 'title' or 'author'
    },
  },
  setup(props) {
    // Optimized book data
    const books = ref([
      {
        id: 1,
        title: "Petar Pan",
        author: "Pero Pavlovic",
        description: "Priča o letećem dječaku.",
        image: "path/to/petar-pan.jpg",
        available: true,
      },
      {
        id: 2,
        title: "Crvenkapica",
        author: "Ivana Brlić-Mažuranić",
        description: "Priča o djevojčici i vuku.",
        image: "path/to/crvenkapica.jpg",
        available: false,
      },
      {
        id: 3,
        title: "Harry Potter",
        author: "J.K. Rowling",
        description: "Priča o mladom čarobnjaku.",
        image: "path/to/harry-potter.jpg",
        available: true,
      },
      {
        id: 4,
        title: "The Hobbit",
        author: "J.R.R. Tolkien",
        description: "Avanture Bilba Bagginsa u Srednjoj Zemlji.",
        image: "path/to/the-hobbit.jpg",
        available: true,
      },
      {
        id: 5,
        title: "To Kill a Mockingbird",
        author: "Harper Lee",
        description: "Priča o rasi i pravdi na američkom Jugu.",
        image: "path/to/to-kill-a-mockingbird.jpg",
        available: false,
      },
      {
        id: 6,
        title: "Pride and Prejudice",
        author: "Jane Austen",
        description: "Klasik o ljubavi i društvenim klasama u Engleskoj.",
        image: "path/to/pride-and-prejudice.jpg",
        available: true,
      },
      {
        id: 7,
        title: "The Great Gatsby",
        author: "F. Scott Fitzgerald",
        description: "Priča o američkom snu i gubitku iluzija.",
        image: "path/to/the-great-gatsby.jpg",
        available: true,
      },
      {
        id: 8,
        title: "Moby Dick",
        author: "Herman Melville",
        description: "Potraga za velikim bijelim kitom po imenu Moby Dick.",
        image: "path/to/moby-dick.jpg",
        available: false,
      },
      {
        id: 9,
        title: "War and Peace",
        author: "Leo Tolstoy",
        description: "Ep o životima tijekom Napoleonskih ratova.",
        image: "path/to/war-and-peace.jpg",
        available: true,
      },
      {
        id: 10,
        title: "1984",
        author: "George Orwell",
        description: "Dystopijski roman o totalitarizmu i nadzoru.",
        image: "path/to/1984.jpg",
        available: true,
      },
      // More books...
    ]);

    // Column definition for the table
    const columns = [
      {
        name: "title",
        required: true,
        label: "Title",
        align: "left",
        field: "title",
      },
      {
        name: "author",
        required: true,
        label: "Author",
        align: "left",
        field: "author",
      },
      {
        name: "description",
        label: "Description",
        align: "left",
        field: "description",
      },
      { name: "image", label: "Image", align: "center", field: "image" },
      {
        name: "available",
        label: "Available",
        align: "center",
        field: "available",
      },
    ];

    // Computed property to filter books based on the searchTerm and filterBy prop
    const filteredBooks = computed(() => {
      if (!props.searchTerm) return books.value;

      const searchTermLower = props.searchTerm.toLowerCase();
      return books.value.filter((book) =>
        props.filterBy === "title"
          ? book.title.toLowerCase().includes(searchTermLower)
          : book.author.toLowerCase().includes(searchTermLower)
      );
    });

    // Watch for prop changes and update filteredBooks accordingly
    watch([props.searchTerm, props.filterBy], () => {
      // Force recompute if needed
    });

    return {
      columns,
      filteredBooks,
    };
  },
};
</script>

<style scoped>
/* Add any component-specific styles here */
</style>
