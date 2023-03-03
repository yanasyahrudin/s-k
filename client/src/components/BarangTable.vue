<template>
  <tr>
    <th scope="row">{{ index + 1 }}</th>
    <td>{{ namaBarang }}</td>
    <td>{{ stok }}</td>
    <td>{{ harga }}</td>
    <td>{{ namaSupplier }}</td>
    <td>{{ alamat }}</td>
    <td>{{ noTelp }}</td>
    <td>
      <button type="button" class="btn btn-primary" @click.prevent="$emit('editBarang', id)">Ubah</button>
      <button type="button" class="btn btn-danger" @click.prevent="$emit('deleteBarang', id)">Hapus</button>
    </td>
  </tr>
</template>
  
<script>
export default {
  name: "BarangTable",
  props: [
    "index",
    "namaBarang",
    "stok",
    "harga",
    "namaSupplier",
    "alamat",
    "noTelp",
    "id",
  ],
  emits: ['editBarang', 'deleteBarang']
};
</script>
  
<style></style>
  