<template>
  <div id="container">
    <Header />
    <div class="space-md"></div>
    <div class="form">
      <div class="label">Quais stickers:</div>
      <div class="space"></div>
      <CheckBox
        :isError="isCheckboxError"
        :value="react"
        @on-change="(newValue) => (react = newValue)"
      >
        React
      </CheckBox>
      <CheckBox
        :isError="isCheckboxError"
        :value="vue"
        @on-change="(newValue) => (vue = newValue)"
      >
        Vue
      </CheckBox>
      <CheckBox
        :isError="isCheckboxError"
        :value="angular"
        @on-change="(newValue) => (angular = newValue)"
      >
        Angular
      </CheckBox>
      <div class="space-md"></div>
      <div class="label">Quantos stickers de cada?</div>
      <div class="space"></div>
      <Contador
        :value="contadorValue"
        :isError="false"
        @aumentar="(v) => (contadorValue = v)"
        @diminuir="(v) => (contadorValue = v)"
      />
      <div class="space-md"></div>
      <div class="label">Observações:</div>
      <div class="space"></div>
      <textarea
        v-model="descricao"
        name="descricao"
        placeholder="Alguma dúvida? Recado?"
      ></textarea>
      <div class="space-md"></div>
    </div>
    <div class="footer">
      <Button @click="validarDados">
        <template #label>Enviar</template>
      </Button>
    </div>
  </div>
</template>

<script>
import Header from "./components/Header/Header.vue";
import CheckBox from "./components/CheckBox/CheckBox.vue";
import Contador from "./components/Contador/Contador.vue";
import Button from "./components/Button/Button.vue";

export default {
  name: "App",
  components: {
    CheckBox,
    Contador,
    Button,
    Header,
  },

  data() {
    return {
      react: false,
      vue: false,
      angular: false,
      contadorValue: 0,
      descricao: "",
      isCheckboxError: false,
    };
  },

  methods: {
    validarDados() {
      if(this.react || this.vue || this.angular) {
        this.isCheckboxError = false
      } else {
        this.isCheckboxError = true
      }
    },
    printValue(contador) {
      console.log(contador);
    },
  },
};
</script>

<style scoped>
* {
  box-sizing: border-box;
  padding: 0;
  margin: 0;
}

#container {
  font-family: sans-serif;
  background-color: #f2f2f2;
  border-radius: 8px;
  box-shadow: 10px 22px 34px 0 rgb(0 0 0 / 50%);
  margin: 20px auto;
  overflow: hidden;
  width: 550px;
}

.form {
  padding: 0px 32px;
}

.form textarea {
  background: #dde3e9;
  border: 1px solid #2f3676;
  border-radius: 8px;
  color: #071723;
  height: 140px;
  padding: 16px;
  resize: none;
  width: 100%;
  font-size: 14px;
}

.label {
  font-size: 18px;
  font-weight: 600;
}

.space-md {
  margin-bottom: 32px;
}

.space {
  margin-bottom: 16px;
}

.footer {
  height: 60px;
  padding: 0 32px;
  background: #dde3e9;
  display: flex;
  justify-content: end;
  align-items: center;
}
</style>
