<template>
  <label>{{ label }}</label>
  <input
    type="text"
    :class="{'error':error}"
    :value="modelValue"
    v-bind="$attrs"
    @input="inputHendler($event)"
    v-maska="bindedObject"
    data-maska="+7 (###)-###-##-##"
    />
  <span v-if="error">{{ error }}</span>
</template>

<script>
import { vMaska } from "maska"

export default {
  name: "CustomPhone",
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
      default: "phone",
    }
  },
  inheritAttrs: false,
  emits: ["update:modelValue"],
  directives: { maska: vMaska },
  data() {
    return {
      error: '',
      bindedObject: {
        masked: '',
        unmasked: '',
        completed: false,
      }
    };
  },
  methods: {
    inputHendler(event) {
      if (!this.bindedObject.completed) {
        this.error = 'Телефон не валидный'
      } else {
        this.error = ''
      }
      this.$emit('update:modelValue', event.target.value)
    },
  }
};
</script>

<style>
input.error {
  border: 1px solid red;
  outline: 1px solid red;
}
</style>
