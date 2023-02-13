<template>
  <div>
    <p>Form</p>
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
        <div class="input-container">
          <label for="opcionais">Escolha os opcionais:</label>
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
            <input
              type="submit"
              class="submit-btn"
              value="Criar meu burguer!"
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
};
</script>

<style scoped></style>
