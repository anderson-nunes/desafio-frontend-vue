<template>
  <button>
    <slot name="label" />
  </button>
</template>

<script>
export default {
  props: {},
};
</script>

<style scoped>
button {
  appearance: none;
  background: #2f3676;
  border: 0;
  border-radius: 7px;
  color: #fff;
  padding: 10px;
  font-size: 18px;
  text-transform: uppercase;
  font-weight: bold;
  padding: 8px 32px;
  cursor: pointer;
  border: 2px solid transparent;
}

button:hover {
  border: 2px solid #2f3676;
  background: #191847;
  color: #fff;
}

button:disabled {
  background: #c5cfd6;
  border: 2px solid #555;
  color: #555;
}
</style>
