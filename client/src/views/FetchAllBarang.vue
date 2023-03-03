<template>
  <div class="mt-4">
    <h1 class="text-center">Barang</h1>
    <div class="text table mb-3">
      <button type="button" class="btn btn-primary" @click.prevent="changePage('AddBarang')">Tambah Barang</button>
    </div>
    <table class="table">
      <thead>
        <tr>
          <th scope="col">No</th>
          <th scope="col">Nama Barang</th>
          <th scope="col">Stok</th>
          <th scope="col">Harga</th>
          <th scope="col">Nama Supplier</th>
          <th scope="col">Alamat Supplier</th>
          <th scope="col">No Telp Supplier</th>
          <th scope="col">Aksi</th>
        </tr>
      </thead>
      <tbody>
        <BarangTable v-for="(item, index) in dataBarang.data" :key="item.id" :index="index" :namaBarang="item.namaBarang"
          :stok="item.stok" :harga="item.harga" :namaSupplier="item.supplier?.namaSupplier"
          :alamat="item.supplier?.alamat" :noTelp="item.supplier?.noTelp" :id="item.id" @editBarang="editBarang" @deleteBarang="deleteBarang"/>
      </tbody>
    </table>
  </div>
</template>
  
<script>
import BarangTable from '../components/BarangTable.vue';

export default {
  components: {
    BarangTable
  },
  emits: ['fetchBarang', 'editBarang', 'deleteBarang','changePage'],
  props: ['dataBarang'],
  methods: {
    editBarang(id){
      this.$emit('editBarang', id)
    },
    deleteBarang(id){
      this.$emit('deleteBarang', id)
    },
    changePage(page) {
      this.$emit('changePage', page)
    }
  },
  created() {
    this.$emit('fetchBarang')
  }
}
</script>
  
<style>
.table {
  width: 100%;
  max-width: 800px;
  margin: 0 auto;
  border-collapse: collapse;
}

th,
td {
  text-align: left;
  padding: 12px;
  border-bottom: 1px solid #ddd;
}

th {
  background-color: #f2f2f2;
  color: #333;
  font-weight: bold;
  text-transform: uppercase;
}

tr:nth-child(even) {
  background-color: #f9f9f9;
}

.text-center {
  text-align: center;
}

.text-right {
  text-align: right;
}

.mb-3 {
  margin-bottom: 1rem;
}
</style>
  