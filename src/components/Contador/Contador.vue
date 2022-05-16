<template>
  <div class="container">
    <Button @click="diminuir" :disabled="buttonDisable">
      <template #label
        ><svg
          xmlns="http://www.w3.org/2000/svg"
          height="24px"
          viewBox="0 0 24 24"
          width="24px"
          fill="#FFFFFF"
        >
          <path d="M0 0h24v24H0z" fill="none" />
          <path d="M19 13H5v-2h14v2z" /></svg
      ></template>
    </Button>
    <input :value="contador" class="input" type="text" />
    <Button @click="aumentar">
      <template #label
        ><svg
          xmlns="http://www.w3.org/2000/svg"
          height="24px"
          viewBox="0 0 24 24"
          width="24px"
          fill="#FFFFFF"
        >
          <path d="M0 0h24v24H0z" fill="none" />
          <path d="M19 13h-6v6h-2v-6H5v-2h6V5h2v6h6v2z" /></svg
      ></template>
    </Button>
  </div>
</template>

<script>
import Button from "../Button/Button.vue";
export default {
  components: {
    Button,
  },
  data() {
    return {
      contador: this.value,
      buttonDisable: false,
    };
  },
  props: {
    value: {
      type: Number,
      default: 0,
    },
    isError: {
      type: Boolean,
      default: false,
    },
  },
  watch: {
    contador() {
      if (this.contador === 0) {
        this.buttonDisable = true;
      } else {
        this.buttonDisable = false;
      }
    },
  },
  methods: {
    aumentar() {
      this.contador = this.contador + 1;
    },

    diminuir() {
      if (this.contador > 0) {
        this.contador = this.contador - 1;
      }
    },
  },
};
</script>

<style scoped>
.container {
  display: flex;
}

button {
  padding: 4px 16px;
}

.input {
  background: #dde3e9;
  border: 1px solid #2f3676;
  border-radius: 4px;
  font-size: 20px;
  font-weight: bold;
  margin: 0 8px;
  width: 50px;
  padding: 8px;
  text-align: center;
  height: 24px;
}
</style>
