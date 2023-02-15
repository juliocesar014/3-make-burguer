<template>
  <div id="burguer-table">
    <h1>Gerenciar Pedidos:</h1>
    <div>
      <div id="burguer-table-heading">
        <div class="order-id">#:</div>
        <div>Cliente:</div>
        <div>Pão:</div>
        <div>Carne:</div>
        <div>Opcionais:</div>
        <div>Ações:</div>
      </div>
    </div>
    <div id="burguer-table-rows" v-for="burguer in burgers" :key="burguer.id">
      <div class="burguer-table-row">
        <div class="order-number">{{ burguer.id }}</div>
        <div>{{ burguer.nome }}</div>
        <div>{{ burguer.pao }}</div>
        <div>{{ burguer.carne }}</div>
        <div>
          <ul>
            <li v-for="(opcional, index) in burguer.opcionais" :key="index">
              {{ opcional }}
            </li>
          </ul>
        </div>
        <div>
          <select name="status" class="status" id="status">
            <option value="" disabled>Selecione</option>
            <option
              value="s.tipo"
              v-for="s in status"
              :key="s.id"
              :selected="burguer.status === s.tipo"
            >
              {{ s.tipo }}
            </option>
          </select>
          <button class="delete-btn">Cancelar</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "DashboardComponente",
  data() {
    return {
      burgers: null,
      burger_id: null,
      status: [],
    };
  },
  methods: {
    async getPedidos() {
      const response = await fetch("http://localhost:3000/burgers");
      const data = await response.json();
      this.burgers = data;
      // Resgatar status
      this.getStatus();
    },

    async getStatus() {
      const response = await fetch("http://localhost:3000/status");
      const data = await response.json();
      this.status = data;
    },
  },
  mounted() {
    this.getPedidos();
  },
};
</script>

<style scoped>
h1 {
  color: #333;
}

#burguer-table {
  max-width: 1200px;
  margin: 0 auto;
}

#burguer-table-heading,
#burguer-table-rows,
.burguer-table-row {
  display: flex;
  flex-direction: wrap;
}

#burguer-table-heading {
  font-weight: bold;
  padding: 12px;
  border-bottom: 3px solid #333;
}

#burguer-table-heading div,
.burguer-table-row div {
  width: 19%;
}

.burguer-table-row {
  width: 100%;
  padding: 12px;
  border-bottom: 1px solid #ccc;
}

#burguer-table-heading .order-id,
.burguer-table-row .order-number {
  width: 5%;
}

select {
  padding: 12px 6px;
  margin-right: 12px;
}

.delete-btn {
  color: #ccc;
  background-color: #222;
  font-size: 16px;
  margin: 0 auto;
  padding: 10px;
}

.delete-btn:hover {
  background: yellow;
  color: #222;
  transition: color 0.3s ease 0s, background 0s ease 0s;
  cursor: pointer;
}
</style>
