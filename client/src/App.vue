<script>
import axios from 'axios'
import FetchAllBarang from './views/FetchAllBarang.vue'
import FetchAllSupplier from './views/FetchAllSupplier.vue'
import Login from './views/Login.vue'
import AddBarang from './views/AddBarang.vue'
import AddSupplier from './views/AddSupplier.vue'
import Navbar from './components/Navbar.vue'
import EditBarang from './views/EditBarang.vue'
import EditSupplier from './views/EditSupplier.vue'
import Register from './views/Register.vue'

let baseUrl = 'http://159.223.57.121:8090'

export default {
  name: 'App',
  data() {
    return {
      currentPage: '',
      dataBarang: [],
      dataSupplier: [],
      idEdit: 0,
      id_edit: 0,
      dataEditBarang: [],
      dataEditSupplier: []
    }
  },
  components: {
    Login,
    FetchAllBarang,
    FetchAllSupplier,
    AddBarang,
    AddSupplier,
    Navbar,
    EditBarang,
    EditSupplier,
    Register
  },
  methods: {
    changePage(page) {
      console.log(page);
      this.currentPage = page
    },
    submitForm(password, profileName, username) {
      axios.post(`${baseUrl}/auth/register`, {
        password: password,
        profileName: profileName,
        username: username
      })
        .then(function (response) {
          console.log(response);
        })
        .catch(function (error) {
          console.log(error);
        })
    },
    loginForm(password, username) {
      axios.post(`${baseUrl}/auth/login`, {
        password: password,
        username: username
      })
        .then((response) => {
          localStorage.setItem('token', 'Bearer ' + response.data.data.token)
          window.location.reload();
        })
        .catch((error) => {
          console.log(error);
        })
    },
    async fetchBarang() {
      try {
        let { data } = await axios({
          method: 'GET',
          url: `${baseUrl}/barang/find-all?limit=20&offset=1`,
          headers: { Authorization: localStorage.getItem('token') }
        })
        this.dataBarang = data
      } catch (error) {
        console.log(error);
      }
    },
    async fetchSupplier() {
      try {
        let { data } = await axios({
          method: 'GET',
          url: `${baseUrl}/supplier/find-all?limit=20&offset=1`,
          headers: { Authorization: localStorage.getItem('token') }
        })
        this.dataSupplier = data
      } catch (error) {
        console.log(error);
      }
    },
    async addBarangForm(namaBarang, stok, harga, namaSupplier, alamat, noTelp) {
      axios({
        method: 'POST',
        url: `${baseUrl}/barang/create`,
        data: {
          namaBarang: namaBarang,
          stok: stok,
          harga: harga,
          supplier: {
            namaSupplier: namaSupplier,
            alamat: alamat,
            noTelp: noTelp
          }
        },
        headers: { Authorization: localStorage.getItem('token') }
      })
        .then((response) => {
          console.log(response);

        })
        .catch((error) => {
          console.log(error);
        })
    },
    async addSupplierForm(namaSupplier, alamat, noTelp) {
      axios({
        method: 'POST',
        url: `${baseUrl}/supplier/create`,
        data: {
          namaSupplier: namaSupplier,
          alamat: alamat,
          noTelp: noTelp
        },
        headers: { Authorization: localStorage.getItem('token') }
      })
        .then((response) => {
          console.log(response);

        })
        .catch((error) => {
          console.log(error);
        })
    },
    async editBarangForm(obj) {
      try {
        await axios({
          method: 'PUT',
          url: `${baseUrl}/barang/update/${this.idEdit}`,
          data: obj,
          headers: {
            Authorization: localStorage.getItem('token')
          }
        })
      } catch (error) {
        console.log(error);
      }
    },
    async editSupplierForm() {
      try {
        await axios({
          method: 'PUT',
          url: `${baseUrl}/supplier/update/${this.id_edit}`,
          data: obj,
          headers: { Authorization: localStorage.getItem('token') }
        })
      } catch (error) {
        console.log(error);
      }
    },
    async editSupplier(id) {
      try {
        let { data } = await axios({
          method: 'PUT',
          url: `${baseUrl}/supplier/update/${id}`,
          headers: { Authorization: localStorage.getItem('token') }
        })
        this.fetchSupplier()
        this.dataEditSupplier = data
        this.currentPage = 'EditSupplier'
        this.id_edit = id
        console.log(this.dataEditSupplier, 'dari edit supplier');
      } catch (error) {
        console.log(error);
      }
    },
    async editBarang(id) {
      try {
        let { data } = await axios({
          method: 'PUT',
          url: `${baseUrl}/barang/update/${id}`,
          headers: {
            Authorization: localStorage.getItem('token')
          }
        })
        this.currentPage = 'EditBarang'
        this.dataEditBarang = data
        this.fetchBarang()
        console.log(data, 'data');
        this.idEdit = id
      } catch (error) {
        console.log(error);
      }
    },
    async deleteBarang(id) {
      try {
        await axios({
          method: 'DELETE',
          url: `${baseUrl}/barang/delete/${id}`,
          headers: { Authorization: localStorage.getItem('token') }
        })
        this.fetchBarang()
      } catch (error) {
        console.log(error);
      }
    },
    async deleteSupplier(id) {
      try {
        await axios({
          method: 'DELETE',
          url: `${baseUrl}/supplier/delete/${id}`,
          headers: { Authorization: localStorage.getItem('token') }
        })
        this.fetchSupplier()
      } catch (error) {
        console.log(error);
      }
    }
  },
  created() {
    if (localStorage.getItem('token')) {
      this.currentPage = 'FetchAllBarang'
      this.currentPage = 'FetchAllSupplier'
    } else {
      this.currentPage = 'Login'
    }
  }
}
</script>

<template>
  <Navbar v-if="currentPage !== 'Register' && currentPage !== 'Login'" @changePage="changePage" />
  <Register v-if="currentPage === 'Register'" @changePage="changePage" @submitForm="submitForm" />
  <Login v-if="currentPage === 'Login'" @changePage="changePage" @loginForm="loginForm" />
  <FetchAllBarang v-if="currentPage === 'FetchAllBarang'" @fetchBarang="fetchBarang" :dataBarang="dataBarang"
    @editBarang="editBarang" @changePage="changePage" @deleteBarang="deleteBarang" />
  <FetchAllSupplier v-if="currentPage === 'FetchAllSupplier'" @fetchSupplier="fetchSupplier" :dataSupplier="dataSupplier"
    @changePage="changePage" @deleteSupplier="deleteSupplier" />
  <AddBarang v-if="currentPage === 'AddBarang'" @changePage="changePage" @addBarangForm="addBarangForm" />
  <AddSupplier v-if="currentPage === 'AddSupplier'" @changePage="changePage" @addSupplierForm="addSupplierForm" />
  <EditBarang v-if="currentPage === 'EditBarang'" @changePage="changePage" :dataEditBarang="dataEditBarang"
    @editBarangForm="editBarangForm" />
  <EditSupplier v-if="currentPage === 'EditSupplier'" @changePage="changePage" :dataEditSupplier="dataEditSupplier"
    @editSupplierForm="editSupplierForm" />
</template>

