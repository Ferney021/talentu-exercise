<script>
import axios from "axios";
export default {
  data() {
    return {
      users: null,
    };
  },
  methods: {
    getUsers() {
      axios.get("https://reqres.in/api/users?page=1").then((res) => {
        console.log(res.data.data);
        this.users = res.data.data;
        localStorage.setItem("users", JSON.stringify(this.users));
      });
    },
    getAge(birthDate) {
      let birth = new Date(birthDate);
      let today = new Date();
      let age = today.getFullYear() - birth.getFullYear();
      let m = today.getMonth() - birth.getMonth();
      if (m < 0 || (m === 0 && today.getDate() < birth.getDate())) {
        age--;
      }
      return age;
    },
    getLastId() {
      let lastId = 0;
      this.users.forEach((user) => {
        if (user.id > lastId) {
          lastId = user.id;
        }
      });
      return lastId;
    },
  },
  mounted() {
    if (localStorage.getItem("users")) {
      this.users = JSON.parse(localStorage.getItem("users"));
    } else {
      this.getUsers();
    }
    this.emitter.on("new-user", (user) => {
      console.log("Esto es lo que esta llegando", user);
      user.id = this.getLastId() + 1;
      user.age = this.getAge(user.birthday);
      this.users.push(user);
      localStorage.setItem("users", JSON.stringify(this.users));
      alert("Usuario registrado correctamente");
    });
  },
};
</script>

<template>
  <div class="card-wrapper user-table">
    <h1>Tabla de Usuarios</h1>
    <div class="tbl-header">
      <table cellpadding="0" cellspacing="0" border="0">
        <thead>
          <tr>
            <th>ID</th>
            <th>Nombre</th>
            <th>Edad</th>
            <th>Email</th>
          </tr>
        </thead>
      </table>
    </div>
    <div class="tbl-content">
      <table cellpadding="0" cellspacing="0" border="0">
        <tbody>
          <tr v-for="(user, u) in users" :key="u">
            <th>{{ user.id }}</th>
            <th>{{ user.first_name }} {{ user.last_name }}</th>
            <th>{{ user.birthday ? user.age : "-" }}</th>
            <th>{{ user.email }}</th>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<style scoped>
h1{
  font-size: 30px;
  color: #fff;
  text-transform: uppercase;
  font-weight: 300;
  text-align: center;
  margin-bottom: 15px;
}
table{
  width:100%;
  table-layout: fixed;
}
.tbl-header{
  background-color: rgba(255,255,255,0.3);
 }
.tbl-content{
  height:300px;
  overflow-x:auto;
  margin-top: 0px;
  border: 1px solid rgba(255,255,255,0.3);
}
th{
  padding: 20px 15px;
  text-align: left;
  font-weight: 500;
  font-size: 12px;
  color: #fff;
  /* text-transform: uppercase; */
}
td{
  padding: 15px;
  text-align: left;
  vertical-align:middle;
  font-weight: 300;
  font-size: 12px;
  color: #fff;
  border-bottom: solid 1px rgba(255,255,255,0.1);
}

/* for custom scrollbar for webkit browser*/

::-webkit-scrollbar {
    width: 6px;
} 
::-webkit-scrollbar-track {
    -webkit-box-shadow: inset 0 0 6px rgba(0,0,0,0.3); 
} 
::-webkit-scrollbar-thumb {
    -webkit-box-shadow: inset 0 0 6px rgba(0,0,0,0.3); 
}
</style>
