<template>
  <div class="container-fluid">
    <Navbar />
    <router-view
      @store="storeData"
      @update="updateData"
      @delete="deleteData"
      :bookList="books"
    />
  </div>
</template>

<script>
import Navbar from "./components/Navbar.vue";

export default {
  name: "App",
  components: {
    Navbar,
  },
  data() {
    return {
      books: [
        {
          _id: 1,
          judul: "Laskar Pelangi",
          pengarang: "Andrea Hirata",
          harga: 80000,
          stok: 7,
        },
        {
          _id: 2,
          judul: "Bumi",
          pengarang: "Tere Liye",
          harga: 85000,
          stok: 5,
        },
      ],
    };
  },
  methods: {
    storeData(bookCreated) {
      console.log(bookCreated);
      alert(`Buku ${bookCreated.judul} berhasil di Simpan !`);
    },
    updateData(bookChanged) {
      console.log(bookChanged);
      alert(`Buku ${bookChanged.judul} berhasil di Ubah !`);
    },
    deleteData(book, index) {
      console.log(book);
      console.log(index);
      alert("Buku berhasil di hapus !");
    },
  },
};
</script>

<style scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
