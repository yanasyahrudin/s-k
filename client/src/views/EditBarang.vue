<script>

export default {
    props: ['dataEditBarang'],
    emits: ['editBarangForm', 'changePage'],
    data() {
        return {
            namaBarang: this.dataEditBarang.namaBarang,
            stok: this.dataEditBarang.stok,
            harga: this.dataEditBarang.harga,
            namaSupplier: this.dataEditBarang.namaSupplier,
            alamat: this.dataEditBarang.alamat,
            noTelp: this.dataEditBarang.noTelp

        }
    },
    methods: {
        editBarangForm() {
            this.$emit('editBarangForm', {
                namaBarang: this.namaBarang,
                stok: this.stok,
                harga: this.harga,
                namaSupplier: this.namaSupplier,
                alamat: this.alamat,
                noTelp: this.noTelp

            })
        },
        changePage() {
            this.$emit('changePage')
        }
    }
}
</script>

<template>
    <div class="add-barang-form">
        <h2>Edit Barang</h2>

        <form v-on:submit.prevent="editBarangForm">
            <div class="form-group">
                <label for="nama-barang">Nama Barang:</label>
                <input type="text" id="nama-barang" v-model="namaBarang" required>
            </div>

            <div class="form-group">
                <label for="stok">Stok:</label>
                <input type="number" id="stok" v-model="stok" required>
            </div>

            <div class="form-group">
                <label for="harga">Harga:</label>
                <input type="number" id="harga" v-model="harga" required>
            </div>

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
                <button type="submit">Tambah Barang</button>
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