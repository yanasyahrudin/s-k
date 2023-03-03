<script>
import SupplierTable from '../components/SupplierTable.vue';

export default {
    name: 'FetchAllSupplier',
    components: {
        SupplierTable
    },
    emits: ['fetchSupplier', 'editSupplier', 'deleteSupplier', 'changePage'],
    props: ['dataSupplier'],
    methods: {
        editSupplier(id) {
            this.$emit('editSupplier', id)
        },
        deleteSupplier(id) {
            this.$emit('deleteSupplier', id)
        },
        changePage(page) {
            this.$emit('changePage', page)
        }
    },
    created() {
        this.$emit('fetchSupplier')
    }
}
</script>
                        
<template>
    <div class="mt-4">
        <h1 class="text-center">Supplier</h1>
        <div class="text table mb-3">
            <button type="button" class="btn btn-primary" @click.prevent="changePage('AddSupplier')">Tambah
                Supplier</button>
        </div>
        <table class="table">
            <thead>
                <tr>
                    <th scope="col">No</th>
                    <th scope="col">Nama Supplier</th>
                    <th scope="col">Alamat Supplier</th>
                    <th scope="col">No Telp Supplier</th>
                    <th scope="col">Aksi</th>
                </tr>
            </thead>
            <tbody>
                <SupplierTable v-for="(item, index) in dataSupplier.data" :key="item.id" :index="index"
                    :namaSupplier="item.namaSupplier" :alamat="item.alamat" :noTelp="item.noTelp" :id="item.id"
                    @editSupplier="editSupplier" @deleteSupplier="deleteSupplier" />
            </tbody>
        </table>
    </div>
</template>
    
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
    