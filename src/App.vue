<template>
  <div id="container">
    <Header />
    <div class="space-md"></div>
    <div class="form">
      <div class="label">Quais stickers:</div>
      <div class="space"></div>
      <CheckBox
        :isError="form.isCheckboxError"
        :value="form.react"
        @on-change="(newValue) => (form.react = newValue)"
      >
        React
      </CheckBox>
      <CheckBox
        :isError="form.isCheckboxError"
        :value="form.vue"
        @on-change="(newValue) => (form.vue = newValue)"
      >
        Vue
      </CheckBox>
      <CheckBox
        :isError="form.isCheckboxError"
        :value="form.angular"
        @on-change="(newValue) => (form.angular = newValue)"
      >
        Angular
      </CheckBox>
      <div class="space-md"></div>
      <div class="label">Quantos stickers de cada?</div>
      <div class="space"></div>
      <Contador
        :value="form.contadorValue"
        :isError="form.isContadorError"
        @aumentar="(v) => (form.contadorValue = v)"
        @diminuir="(v) => (form.contadorValue = v)"
      />
      <div class="space-md"></div>
      <div class="label">Observações:</div>
      <div class="space"></div>
      <textarea
        v-model="form.descricao"
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
      form: {
        react: false,
        vue: false,
        angular: false,
        contadorValue: 0,
        descricao: "",
        isCheckboxError: false,
        isContadorError: false,
      },
    };
  },

  watch: {
    form: {
      handler() {
        this.validarDados();
      },
      deep: true,
    },
  },

  methods: {
    validarDados() {
      if (this.form.react || this.form.vue || this.form.angular) {
        this.form.isCheckboxError = false;
      } else {
        this.form.isCheckboxError = true;
      }
      if (this.form.contadorValue > 0) {
        this.form.isContadorError = false;
      } else {
        this.form.isContadorError = true;
      }
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
