<template>
  <div>
    <div>
      <form id="burguer-form">
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
            <option value="integral">Integral</option>
          </select>
        </div>
        <div class="input-container">
          <label for="carne">Escolha a carne:</label>
          <select name="carne" id="carne" v-model="carne">
            <option value="">Selecione a sua carne</option>
            <option value="maminha">Maminha</option>
          </select>
        </div>
        <div class="input-container" id="opcionais-container">
          <label id="opcionais-title" for="opcionais"
            >Escolha os opcionais:</label
          >
          <div class="checkbox-container">
            <input
              type="checkbox"
              name="opcionais"
              v-model="opcionais"
              value="salame"
            />
            <span>Salame</span>
          </div>
          <div class="input-container">
            <input type="submit" class="submit-btn" value="Criar meu burguer" />
          </div>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: "FormComponente",
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
