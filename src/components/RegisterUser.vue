<script>
export default {
  data() {
    return {
      user: {
        first_name: "",
        last_name: "",
        email: "",
        birthday: "",
      },
    };
  },
  methods: {
    registerUser() {
      this.emitter.emit("new-user", this.user);
      this.user = {
        first_name: "",
        last_name: "",
        email: "",
        birthday: "",
      };
    },
  }
}
</script>

<template>
  <div class="card-wrapper register-form">
    <div class="register-form-title">
      <h1>Registro</h1>
    </div>
    <div class="register-form-inputs">
      <div class="register-form-inputs-item">
        <span>Email:</span>
        <input
          type="text"
          id="email"
          placeholder="ej@mail.com"
          v-model="user.email"
        />
      </div>
      <div class="register-form-inputs-item">
        <span>Nombre:</span>
        <input type="text" id="name" placeholder="..." v-model="user.first_name" />
      </div>
      <div class="register-form-inputs-item">
        <span>Apellido:</span>
        <input
          type="text"
          id="lastname"
          placeholder="..."
          v-model="user.last_name"
        />
      </div>
      <div class="register-form-inputs-item">
        <span>Fecha de Nacimiento:</span>
        <input
          type="date"
          id="birth"
          placeholder="Fecha de Nacimiento"
          v-model="user.birthday"
        />
      </div>
    </div>
    <div class="register-form-button">
      <button type="button" @click="registerUser" class="btn">
        Agregar Usuario
      </button>
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
.register-form {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  width: 100%;
  height: 100%;
  /* border: 1px solid #ccc; */
}
.register-form-inputs {
  width: 100%;
  margin-top: 20px;
}
.register-form-inputs-item {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  width: 100%;
  height: 100%;
  font-size: 12px;
}
.register-form-inputs-item > input {
  width: 100%;
  font-size: 20px;
  padding: 20px;
  border: 1px solid #fff;
  outline: none;
  border-radius: 20px;
  margin: 10px;
  text-align: center;
  /* background: rgba(183, 183, 183, 0.3); */
  background: transparent;
  color: #fff;
}
.register-form-inputs-item > input::placeholder {
  text-align: center;
  color: rgba(255, 255, 255, 0.311);
}
.btn {
  width: 100%;
  font-size: 12px;
  padding: 20px;
  border: 1px solid #fff;
  outline: none;
  border-radius: 20px;
  margin: 10px;
  text-align: center;
  background: rgba(183, 183, 183, 0.3);
  color: #fff;
}
.btn:hover {
  background: rgba(183, 183, 183, 0.5);
  cursor: pointer;
}
</style>
