<script>
export default {
  name: 'Navbar',
  components: {
  },
  emits: ['changePage', 'fetchBarang', 'fetchSupplier'],
  methods: {
    changePage(page) {
      this.$emit('changePage', page)
    },
    logout() {
      localStorage.clear()
      window.location.reload();
    },
  }
}
</script>

<template>
  <nav class="navbar navbar-expand-lg navbar-dark bg-primary">
    <div class="container-fluid">
      <a class="navbar-brand" href="#">Dashboard</a>
      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav"
        aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarNav">
        <ul class="navbar-nav ms-auto">
          <li class="nav-item">
            <a class="nav-link" href="#" @click.prevent="changePage('FetchAllBarang')">Barang</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#" @click.prevent="changePage('FetchAllSupplier')">Supplier</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#" @click.prevent="logout">Logout</a>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>
  
<style>
.navbar {
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.navbar-brand {
  font-weight: bold;
  font-size: 1.5rem;
}

.navbar-nav {
  font-size: 1.2rem;
}

.nav-link {
  padding: 0.5rem 1rem;
}
</style>
  