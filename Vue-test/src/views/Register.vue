<template>
  <div class="default">
    <div class="register-box">
      <form class="register-form" @submit="createUser">
        <div class="input-container">
          <h1>Cadastrar Usuário</h1>
          <label for="name">Nome:</label>
          <input
            type="text"
            id="name"
            name="name"
            v-model="name"
            placeholder=""
          />
        </div>
        <div class="input-container">
          <label for="company">Empresa:</label>
          <input
            type="text"
            id="company"
            name="company"
            v-model="company"
            placeholder=""
          />
        </div>
        <div class="input-container">
          <label for="city">Cidade:</label>
          <input
            type="text"
            id="city"
            name="city"
            v-model="city"
            placeholder=""
          />
        </div>
        <div class="input-container">
          <label for="phone">Telefone:</label>
          <input
            type="text"
            id="phone"
            name="phone"
            v-model="phone"
            placeholder=""
          />
        </div>
        <div class="input-container">
          <div class="button-box">
            <router-link to="/">
              <button class="cancel-button">Cancelar</button>
            </router-link>
            <input type="submit" value="Cadastrar" class="submit-button" />
          </div>
        </div>
      </form>
    </div>
  </div>
</template>
<script>
export default {
  name: "Register",
  data() {
    return {
      users: null,
    };
  },
  methods: {
    async createUser(e) {
      e.preventDefault();

      const data = {
        name: this.name,
        company: this.company,
        city: this.city,
        phone: this.phone,
      };
      const dataJson = JSON.stringify(data);

      const req = await fetch("http://localhost:3000/users", {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: dataJson,
      });

      const res = await req.json();
      this.$router.push("/");
    },
  },
};
</script>
<style>
.default {
  display: flex;
  justify-content: center;
  align-items: center;
  height: auto;
  font-family: "Gill Sans", "Gill Sans MT", Calibri, "Trebuchet MS", sans-serif;
}
.register-box {
  background-color: #fff;
  display: flex;
  flex-direction: column;
  box-sizing: border-box;
  width: 35rem;
  height: 40rem;
  border-radius: 9px;
  margin-top: 5rem;
}
.input-container {
  display: flex;
  flex-direction: column;
  padding: 1rem;
}
.submit-button {
  height: 3.5rem;
  width: 12rem;
  margin: 0 1rem 0 1rem;
  border: none;
  background-color: #f7c04a;
  border-radius: 6px;
  color: #fff;
  font-weight: bold;
  font-size: 1rem;
}
.button-box {
  display: flex;
  justify-content: space-around;
  margin-top: 2rem;
}
.cancel-button {
  height: 3.5rem;
  width: 12rem;
  margin: 0 0 0 1rem;
  border: none;
  background-color: #ff0303;
  border-radius: 6px;
  color: #fff;
  font-weight: bold;
  font-size: 1rem;
}
input {
  margin-top: 1rem;
  border-radius: 4px;
  height: 1.5rem;
}
label {
  font-weight: bold;
}
h1 {
  align-self: center;
  font-weight: bold;
}
</style>
