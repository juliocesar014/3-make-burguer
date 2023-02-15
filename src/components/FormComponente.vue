<template>
  <div>
    <div>
      <form id="burguer-form" @submit="createBurguer">
        <div class="input-container">
          <label for="nome">Nome do Cliente:</label>
          <input
            type="text"
            id="nome"
            name="nome"
            v-model="nome"
            placeholder="Digite seu nome"
          />
        </div>
        <div class="input-container">
          <label for="pao">Escolha o pão:</label>
          <select name="pao" id="pao" v-model="pao">
            <option value="">Selecione o seu pão</option>
            <option v-for="pao in paes" :key="pao.id" :value="pao.tipo">
              {{ pao.tipo }}
            </option>
          </select>
        </div>
        <div class="input-container">
          <label for="carne">Escolha a carne:</label>
          <select name="carne" id="carne" v-model="carne">
            <option value="">Selecione a sua carne</option>
            <option v-for="carne in carnes" :key="carne.id" :value="carne.tipo">
              {{ carne.tipo }}
            </option>
          </select>
        </div>
        <div class="input-container" id="opcionais-container">
          <label id="opcionais-title" for="opcionais"
            >Escolha os opcionais:</label
          >
          <div
            class="checkbox-container"
            v-for="opcional in opcionaisdata"
            :key="opcional.id"
          >
            <input
              type="checkbox"
              name="opcionais"
              v-model="opcionais"
              :value="opcional.tipo"
            />
            <span>{{ opcional.tipo }}</span>
          </div>
          <div class="input-container">
            <input
              type="submit"
              class="submit-btn"
              value="Criar meu burguer"
              @click="showAlert"
            />
          </div>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: "FormComponente",
  data() {
    return {
      paes: null,
      carnes: null,
      opcionaisdata: null,
      nome: null,
      pao: null,
      carne: null,
      opcionais: [],
      msg: null,
    };
  },
  methods: {
    showAlert() {
      Swal.fire("Sucesso!", "Hamburguer criado com sucesso", "success");
    },
    async getIngredients() {
      const response = await fetch("http://localhost:3000/ingredientes");
      const data = await response.json();

      this.paes = data.paes;
      this.carnes = data.carnes;
      this.opcionaisdata = data.opcionais;
    },

    async createBurguer(e) {
      e.preventDefault();

      const burguer = {
        nome: this.nome,
        pao: this.pao,
        carne: this.carne,
        opcionais: Array.from(this.opcionais),
        status: "Solicitado",
      };
      const burguerJson = JSON.stringify(burguer);

      const response = await fetch("http://localhost:3000/burgers", {
        method: "POST",
        headers: {
          "Content-Type": "application/json",
        },
        body: burguerJson,
      });
      // Enviar a requisição para a API

      // Limpar os campos do formulário - Após preencher o formulário.
      (this.nome = ""),
        (this.pao = ""),
        (this.carne = ""),
        (this.opcionais = []);

      const data = await response.json();
      console.log(data);
    },
  },

  mounted() {
    this.getIngredients();
  },
};
</script>

<style scoped>
#burguer-form {
  max-width: 400px;
  margin: 0 auto;
}

.input-container {
  display: flex;
  flex-direction: column;
  margin-bottom: 20px;
}

label {
  font-weight: bold;
  margin-bottom: 15px;
  color: #222;
  padding: 5px 10px;
  border-left: 4px solid yellow;
}

input,
select {
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 2px;
  outline: none;
}

.submit-btn {
  color: #ccc;
  background-color: #222;
  font-size: 16px;
  margin: 0 auto;
  padding: 10px;
}

.submit-btn:hover {
  background: yellow;
  color: #222;
  transition: color 0.3s ease 0s, background 0s ease 0s;
  cursor: pointer;
}

#opcionais-container {
  flex-direction: row;
  flex-wrap: wrap;
}

#opcionais-title {
  width: 100%;
}

.checkbox-container {
  display: flex;
  align-items: center;
  width: 50%;
  margin-bottom: 20px;
}

.checkbox-container input,
span {
  width: auto;
}

.checkbox-container span {
  margin-left: 6px;
  font-weight: bold;
}
</style>
