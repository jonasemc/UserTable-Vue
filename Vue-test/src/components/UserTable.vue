<template>
  <div class="screen">
    <h1>Tabela de Usuários</h1>
    <div class="button-box">
      <RouterLink to="Register">
        <button class="add-button">Adicionar Usuário</button>
      </RouterLink>
      <button class="remove-button">Remover Usuário</button>
    </div>
    <div class="table-box">
      <table>
        <thead>
          <tr>
            <th>Usuário</th>
            <th>Empresa</th>
            <th>Cidade</th>
            <th>Telefone</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="user in users" :key="user.id">
            <td>{{ user.name }}</td>
            <td>{{ user.company }}</td>
            <td>{{ user.city }}</td>
            <td>{{ user.phone }}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
export default {
  name: "UserTable",
  data() {
    return {
      users: null,
    };
  },
  methods: {
    async getUsers() {
      const req = await fetch("http://localhost:3000/users");
      const data = await req.json();

      this.users = data;
    },
  },
  mounted() {
    this.getUsers();
  },
};
</script>

<style scoped>
.screen {
  display: flex;
  flex-direction: column;
  align-items: center;
  font-family: "Gill Sans", "Gill Sans MT", Calibri, "Trebuchet MS", sans-serif;
}
h1 {
  font-weight: bold;
}

.button-box {
  width: 100%;
  display: flex;
  padding: 2rem;
  justify-content: flex-end;
}
.add-button {
  height: 3.5rem;
  width: 12rem;
  margin: 0 1rem 0 1rem;
  border: none;
  background-color: #f7c04a;
  border-radius: 6px;
  color: #1b1b1b;
  font-weight: bold;
  font-size: 0.9rem;
  cursor: pointer;
}
.remove-button {
  height: 3.5rem;
  width: 12rem;
  margin: 0 0 0 1rem;
  border: none;
  background-color: #ff0303;
  border-radius: 6px;
  color: #fff;
  font-weight: bold;
  font-size: 0.9rem;
  cursor: pointer;
}

table,
th,
td {
  height: 3rem;
  text-align: center;
  color: #1b1b1b;
}

th,
td {
  border: solid 1px #fff;
  background-color: #fff;
  border-radius: 4px;
}

table {
  width: 100%;
  align-items: center;
}

.table-box {
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
