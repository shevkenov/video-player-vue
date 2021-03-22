<template>
  <div>
    <input type="text" @input="onInput"/>
  </div>
</template>

<script>
export default {
  name: "SearchBar",
  data: function () {
    return {
      searchedData: "",
    };
  },
  methods: {
    onInput: function ({target}) {
        this.$emit('termChange', target.value);
    },
  },
};
</script>

<style scoped>
    input {
        width: 75%
    }

    div {
        text-align: center;
        margin: 20px;
    }
</style>