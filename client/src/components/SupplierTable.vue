    
<script>
export default {
  name: "SupplierTable",
  props: [
    "index",
    "namaSupplier",
    "alamat",
    "noTelp",
    "id",
  ],
  emits: ['editSupplier', 'deleteSupplier']
};
</script>
    
<template>
  <tr>
    <th scope="row">{{ index + 1 }}</th>
    <td>{{ namaSupplier }}</td>
    <td>{{ alamat }}</td>
    <td>{{ noTelp }}</td>
    <td>
      <button type="button" class="btn btn-primary" @click.prevent="$emit('editSupplier', id)">Ubah</button>
      <button type="button" class="btn btn-danger" @click.prevent="$emit('deleteSupplier', id)">Hapus</button>
    </td>
  </tr>
</template>
  
<style></style>
    