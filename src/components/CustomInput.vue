<template>
  <label>{{ label }}</label>
  <input
    type="text"
    :class="{'error':error}"
    :value="modelValue"
    v-bind="$attrs"
    @input="inputHendler($event)"
  />
  <span v-if="error">{{ error }}</span>
</template>

<script>
export default {
  name: "CustomInput",
  props: {
    modelValue: {
      type: String,
      default: "",
    },
    label: {
      type: String,
      default: "",
    },
    type: {
      type: String,
      default: "text",
    }
  },
  inheritAttrs: false,
  emits: ["update:modelValue"],
  data() {
    return {
      error: '',
    };
  },
  methods: {
    inputHendler(event) {
      if (this.type === 'email') {
        if (!this.emailRegexp(event.target.value)) {
          this.error = 'Email не валидный';
        } else {
          this.error = '';
        }
      }
      this.$emit('update:modelValue', event.target.value)
    },
    emailRegexp(value) {
      return /^(([^<>()[\].,;:\s@"]+(\.[^<>()[\].,;:\s@"]+)*)|(".+"))@(([^<>()[\].,;:\s@"]+\.)+[^<>()[\].,;:\s@"]{2,})$/iu.test(value);
    }
  }
};
</script>

<style>
input.error {
  border: 1px solid red;
  outline: 1px solid red;
}
</style>
