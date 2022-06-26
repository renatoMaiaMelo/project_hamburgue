<template>
  <div>
    <p>Component de mensagem</p>
    <div>
      <form id="burger_form">
        <div class="input_container">
          <label for="nome">Nome do cliente:</label>
          <input
            type="text"
            id="nome"
            name="name"
            v-model="nome"
            placeholder="Digite o seu nome"
          />
        </div>

        <div class="input_container">
          <label for="pao">Escolha o pão:</label>
          <select name="pao" id="pao" v-model="pao">
            <option value="">Selecione o seu pão</option>
            <option v-for="pao in paes" :key="pao.id" :value="pao.tipo">
              {{ pao.tipo }}
            </option>
          </select>
        </div>

        <div class="input_container">
          <label for="carne">Escolha a do seu burger:</label>
          <select name="carne" id="carne" v-model="carne">
            <option value="">Selecione a sua carne</option>
            <option v-for="carne in carnes" :key="carne.id" :value="carne.tipo">
              {{ carne.tipo }}
            </option>
          </select>
        </div>

        <div id="opcionais_container" class="input_container">
          <label id="opcionais_title" for="opcionais"
            >Selecione os opcionais:</label
          >
          <div
            v-for="opcional in opcionaisdata"
            :key="opcional.id"
            class="checkbox_container"
          >
            <input
              type="checkbox"
              name="opcionais"
              id="opcionais"
              v-model="opcionais"
              :value="opcional.tipo"
            />
            <span>{{ opcional.tipo }}</span>
          </div>
        </div>

        <div class="input_container">
          <input class="submit_btn" type="submit" value="Criar meu Burger!" />
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: "BurgerForm",
  data() {
    return {
      paes: null,
      carnes: null,
      opcionaisdata: null,
      nome: null,
      pao: null,
      carne: null,
      opcionais: [],
      status: "Solicitado",
      msg: null,
    };
  },

  methods: {
    async getIngredientes() {
      const req = await fetch("http://localhost:3000/ingredientes");
      const data = await req.json();

      this.paes = data.paes;
      this.carnes = data.carnes;
      this.opcionaisdata = data.opcionais;
    },
  },

  mounted() {
    this.getIngredientes();
  },
};
</script>

<style scoped>
#burger_form {
  max-width: 400px;
  margin: 0 auto;
}

#burger_form .input_container {
  display: flex;
  flex-direction: column;
  margin-bottom: 20px;
}

#burger_form .input_container label {
  font-weight: bold;
  margin-bottom: 15px;
  color: #222;
  padding: 5px 10px;
  border-left: 4px solid #fcba03;
}

#burger_form .input_container input,
select {
  padding: 5px 10px;
  width: 300px;
}

#burger_form #opcionais_container {
  flex-direction: row;
  flex-wrap: wrap;
}

#burger_form .input_container #opcionais_title {
  width: 100%;
}

#burger_form .input_container .checkbox_container {
  display: flex;
  align-items: flex-start;
  width: 50%;
  margin-bottom: 20px;
}

#burger_form .input_container .checkbox_container span,
#burger_form .input_container .checkbox_container input {
  width: auto;
}

#burger_form .input_container .checkbox_container span {
  margin-left: 6px;
  font-weight: bold;
}

#burger_form .input_container .submit_btn {
  background-color: #222;
  color: #fcba03;
  font-weight: bold;
  border: 2px solid #222;
  padding: 10px;
  font-size: 16px;
  margin: 0 auto;
  cursor: pointer;
  transition: 0.5s;
}

#burger_form .input_container .submit_btn:hover {
  background-color: transparent;
  color: #222;
}
</style>