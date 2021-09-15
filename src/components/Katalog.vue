<template>
  <div class="container mt-3 w-75">
    <h1 class="text-center">Selamat datang di toko buku Camp404</h1>
    <div id="katalogBuku">
      <h2 class="text-center">Katalog Buku</h2>
      <hr />
      <table class="table table-bordered">
        <thead>
          <tr class="text-center">
            <th>No.</th>
            <th>Judul</th>
            <th>Pengarang</th>
            <th>Harga</th>
            <th>Stok</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(book, index) in bookList" :key="index">
            <td class="text-center">{{ index + 1 }}</td>
            <td>{{ book.judul }}</td>
            <td>{{ book.pengarang }}</td>
            <td>{{ book.harga }}</td>
            <td>{{ book.stok }}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
export default {
  props: ["bookList"],
};
</script>

<style></style>
