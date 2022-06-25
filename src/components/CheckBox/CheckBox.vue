<template>
  <label>
    <slot />
    <input class="checkbox" type="checkbox" v-model="checked" />
    <span :class="['checkmark', { error: isError }]"></span>
  </label>
</template>

<script>
export default {
  data() {
    return {
      checked: this.value,
    };
  },
  props: {
    value: {
      type: Boolean,
      default: false,
    },
    isError: {
      type: Boolean,
      default: false,
    },
  },
  watch: {
    checked() {
      this.$emit("on-change", this.checked);
    },
  },
};
</script>

<style scoped>
label {
  display: block;
  position: relative;
  padding-left: 35px;
  margin-bottom: 12px;
  cursor: pointer;
  font-size: 22px;
  user-select: none;
}

label input {
  position: absolute;
  opacity: 0;
  cursor: pointer;
  height: 0;
  width: 0;
}

label:hover input ~ .checkmark {
  background-color: #191847;
}

label input:checked ~ .checkmark {
  background-color: #2f3676;
}
.checkmark {
  position: absolute;
  top: 0;
  left: 0;
  height: 25px;
  width: 25px;
  background-color: #2f3676;
  border-radius: 5px;
}

.checkmark:after {
  content: "";
  position: absolute;
  display: none;
}

label input:checked ~ .checkmark:after {
  display: block;
}

label .checkmark:after {
  left: 9px;
  top: 5px;
  width: 5px;
  height: 10px;
  border: solid white;
  border-width: 0 3px 3px 0;
  -webkit-transform: rotate(45deg);
  -ms-transform: rotate(45deg);
  transform: rotate(45deg);
}

label .checkmark.error {
  background-color: #f59393;
}
</style>
