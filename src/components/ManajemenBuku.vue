<template>
  <div class="container mt-3 w-75">
    <h1 class="text-center">Manajemen Buku</h1>
    <!-- awal form tambah -->
    <div id="formTambah" v-if="formMode == 'create'">
      <h5 class="text-center">Form Tambah</h5>
      <hr />
      <form class="row" @submit.prevent="submitAdd">
        <div class="col-md-3 mt-2 mb-2">
          <input
            type="text"
            class="form-control "
            placeholder="Judul"
            v-model="newBook.judul"
          />
        </div>
        <div class="col-md-3">
          <input
            type="text"
            class="form-control mt-2 mb-2"
            placeholder="Pengarang"
            v-model="newBook.pengarang"
          />
        </div>
        <div class="col-md-2">
          <input
            type="text"
            class="form-control mt-2 mb-2"
            placeholder="Harga"
            v-model="newBook.harga"
          />
        </div>
        <div class="col-md-2">
          <input
            type="text"
            class="form-control mt-2 mb-2"
            placeholder="Stok"
            v-model="newBook.stok"
          />
        </div>
        <div class="col-md-2 text-center mt-2 mb-2">
          <input
            type="submit"
            value="Simpan"
            class="btn btn-sm btn-primary ml-5"
          />
        </div>
      </form>
    </div>
    <!-- Akhir form tambah -->

    <!-- awal form Ubah -->
    <div id="formUbah" v-if="formMode == 'edit'">
      <h5 class="text-center">Form Ubah</h5>
      <hr />
      <form class="row" @submit.prevent="submitChange">
        <div class="col-md-3 mt-2 mb-2">
          <input
            type="text"
            class="form-control "
            placeholder="Judul"
            v-model="updatedBook.judul"
          />
        </div>
        <div class="col-md-3">
          <input
            type="text"
            class="form-control mt-2 mb-2"
            placeholder="Pengarang"
            v-model="updatedBook.pengarang"
          />
        </div>
        <div class="col-md-2">
          <input
            type="text"
            class="form-control mt-2 mb-2"
            placeholder="Harga"
            v-model="updatedBook.harga"
          />
        </div>
        <div class="col-md-2">
          <input
            type="text"
            class="form-control mt-2 mb-2"
            placeholder="Stok"
            v-model="updatedBook.stok"
          />
        </div>
        <div class="col-md-2 text-center mt-2 mb-2">
          <input
            type="submit"
            value="Simpan"
            class="btn btn-sm btn-primary ml-5"
          />
        </div>
      </form>
    </div>
    <!-- akhir form ubah -->

    <!-- awal daftar buku -->
    <div id="daftarBuku">
      <h2 class="text-center">Daftar Buku</h2>
      <hr />
      <div class="text-center p-3">
        <button @click="formMode = 'create'" class="btn btn-primary">
          Tambah Buku
        </button>
      </div>

      <table class="table table-bordered">
        <thead>
          <tr class="text-center">
            <th>No.</th>
            <th>Judul</th>
            <th>Pengarang</th>
            <th>Harga</th>
            <th>Stok</th>
            <th>Aksi</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(book, index) in bookList" :key="index">
            <td class="text-center">{{ index + 1 }}</td>
            <td>{{ book.judul }}</td>
            <td>{{ book.pengarang }}</td>
            <td>{{ book.harga }}</td>
            <td>{{ book.stok }}</td>
            <td class="text-center">
              <button
                class="btn btn-sm btn-info"
                @click="showEdit(book, index)"
              >
                Edit
              </button>
              <button
                class="btn btn-sm btn-danger"
                @click="deleteBook(book, index)"
              >
                Hapus
              </button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
    <!-- Akhir daftar buku -->
  </div>
</template>

<script>
export default {
  props: ["bookList"],
  data() {
    return {
      newBook: {
        judul: "",
        pengarang: "",
        harga: "",
        stok: "",
      },

      formMode: "",
      bookIndex: "",

      updatedBook: {
        _id: "",
        judul: "",
        pengarang: "",
        harga: "",
        stok: "",
      },
    };
  },
  methods: {
    submitAdd() {
      const bookCreated = {
        judul: this.newBook.judul,
        pengarang: this.newBook.pengarang,
        harga: this.newBook.harga,
        stok: this.newBook.stok,
      };
      //mengirim data dari child ke parent $emit
      // console.log(bookCreated);
      this.$emit("store", bookCreated);

      //reset input form tambah
      this.newBook.judul = "";
      this.newBook.pengarang = "";
      this.newBook.harga = "";
      this.newBook.stok = "";

      //hide form tambah
      this.formMode = "";
    },

    showEdit(book, index) {
      this.formMode = "edit";
      this.bookIndex = index;

      this.updatedBook._id = book._id;
      this.updatedBook.judul = book.judul;
      this.updatedBook.pengarang = book.pengarang;
      this.updatedBook.harga = book.harga;
      this.updatedBook.stok = book.stok;
    },

    submitChange() {
      const bookChanged = this.updatedBook;

      this.$emit("update", bookChanged, this.bookIndex);
      this.formMode = "";
    },

    deleteBook(book, index) {
      this.$emit("delete", book, index);
    },
  },
};
</script>

<style></style>
