<template>
  <div class="container-fluid">
    <nav class="navbar navbar-expand navbar-dark bg-primary">
      <a class="navbar-brand" href="#">CAMP404</a>
      <button
        class="navbar-toggler d-lg-none"
        type="button"
        data-toggle="collapse"
        data-target="#collapsibleNavId"
        aria-controls="collapsibleNavId"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="collapsibleNavId">
        <ul class="navbar-nav mr-auto mt-2 mt-lg-0">
          <li class="nav-item active">
            <router-link to="/" class="nav-link">Katalog</router-link>
          </li>
          <li class="nav-item">
            <router-link to="/manajemen-buku" class="nav-link"
              >Manajemen Buku</router-link
            >
          </li>
        </ul>
      </div>
    </nav>
  </div>
</template>

<script>
export default {};
</script>

<style scoped>
.navbar {
  padding-left: 20px;
}
</style>
