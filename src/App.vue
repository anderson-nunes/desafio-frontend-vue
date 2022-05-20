<template>
  <div id="container">
    <Header />
    <div id="form">
      <h2>Quais stickers:</h2>
      <CheckBox :value="react" @on-change="(newValue) => (react = newValue)">
        React
      </CheckBox>
      <CheckBox :value="vue" @on-change="(newValue) => (vue = newValue)">
        Vue
      </CheckBox>
      <CheckBox
        :value="angular"
        @on-change="(newValue) => (angular = newValue)"
      >
        Angular
      </CheckBox>
      <h2>Quantos stickers de cada?</h2>
      <Contador
        :value="0"
        :isError="false"
        @aumentar="(v) => {}"
        @diminuir="(v) => {}"
      />
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
    };
  },

  methods: {
    validarDados() {
      console.log("okkk");
    },
  },
};
</script>

<style scoped>
#container {
  background-color: #f2f2f2;
  border-radius: 8px;
  box-shadow: 10px 22px 34px 0 rgb(0 0 0 / 50%);
  margin: 20px auto;
  overflow: hidden;
  width: 550px;
}

#form {
  padding: 0px 32px;
}
</style>
