<template>
  <div class="input-group flex-nowrap">
    <span class="input-group-text" id="addon-wrapping">@</span>
    <input
      type="text"
      class="form-control"
      v-model="textInput"
      :placeholder="placeholderText"
      :aria-label="placeholderText"
      aria-describedby="addon-wrapping"
      @input="changeSubmitState"
    />
  </div>
</template>

<script>
export default {
  props: {
    placeholderText: {
      type: String,
      default: "",
    },
    isSubmit: {
      type: Boolean,
      default: false,
    },
  },
  data() {
    return {
      textInput: "",
    };
  },
  watch: {
    textInput() {
      this.$emit("onChange", this.textInput);
    },
    isSubmit() {
      if (this.isSubmit) {
        this.textInput = "";
      }
    },
  },
  methods: {
    changeSubmitState() {
      if (this.isSubmit) this.$emit("changeSubmitState", false);
    },
  },
};
</script>

<style></style>
