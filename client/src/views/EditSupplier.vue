<script>

export default {
    props: ['dataEditSupplier'],
    emits: ['editSupplierForm', 'changePage'],
    data() {
        return {
            namaSupplier: this.dataEditSupplier.namaSupplier,
            alamat: this.dataEditSupplier.alamat,
            noTelp: this.dataEditSupplier.noTelp
        }
    },
    methods: {
        editSupplierForm() {
            this.$emit('editSupplierForm', { namaSupplier: this.namaSupplier, alamat: this.alamat, noTelp: this.noTelp })
        },
        changePage(){
            this.$emit('changePage')
        }
    }
}
</script>

<template>
    <div class="add-barang-form">
        <h2>Edit Supplier</h2>

        <form v-on:submit.prevent="editSupplierForm" >
            <div class="form-group">
                <label for="nama-supplier">Nama Supplier:</label>
                <input type="text" id="nama-supplier" v-model="namaSupplier" required>
            </div>

            <div class="form-group">
                <label for="alamat">Alamat Supplier:</label>
                <input type="text" id="alamat" v-model="alamat" required>
            </div>

            <div class="form-group">
                <label for="no-telp">No. Telp Supplier:</label>
                <input type="text" id="no-telp" v-model="noTelp" required>
            </div>

            <div class="form-group">
                <button type="submit">Tambah Supplier</button>
            </div>
        </form>
    </div>
</template>

<style scoped>
.add-barang-form {
    max-width: 500px;
    margin: 0 auto;
    padding: 20px;
    background-color: #f5f5f5;
    border-radius: 5px;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.3);
}

.add-barang-form h2 {
    text-align: center;
    margin-bottom: 20px;
}

.form-group {
    margin-bottom: 10px;
}

label {
    display: block;
    font-weight: bold;
    margin-bottom: 5px;
}

input[type="text"],
input[type="number"] {
    width: 100%;
    padding: 8px;
    border: 1px solid #ccc;
    border-radius: 3px;
    font-size: 16px;
}

button[type="submit"] {
    background-color: #4caf50;
    color: #fff;
    border: none;
    border-radius: 3px;
    padding: 10px 20px;
    font-size: 16px;
    cursor: pointer;
}
</style>