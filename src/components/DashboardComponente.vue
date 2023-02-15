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
    <div id="burguer-table-rows">
      <div class="burguer-table-row">
        <div class="order-number">1</div>
        <div>Nome do Cliente</div>
        <div>Pão 01</div>
        <div>Carne 01</div>
        <div>
          <li>Salame</li>
          <li>Tomate</li>
        </div>
        <div>
          <select name="status" class="status" id="">
            <option value="">Selecione</option>
          </select>
          <button class="delete-btn">Cancelar</button>
        </div>
      </div>
    </div>
    <div id="burguer-table-rows">
      <div class="burguer-table-row">
        <div class="order-number">1</div>
        <div>Nome do Cliente</div>
        <div>Pão 01</div>
        <div>Carne 01</div>
        <div>
          <li>Salame</li>
          <li>Tomate</li>
        </div>
        <div>
          <select name="status" class="status" id="">
            <option value="">Selecione</option>
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
