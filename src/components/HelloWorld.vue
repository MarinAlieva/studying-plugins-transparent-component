<template>
  <h2>Transparent input wrapper</h2>

  <div class="row">
    <CustomInput
      v-model="text"
      label="Type text"
      class="text"
      type="text"
      />

    <CustomInput
      v-model="email"
      label="Type email"
      class="email"
      type="email"
    />

    <CustomPhone
      v-model="phone"
      label="Type phone"
      class="phone"
      type="phone"
    />
  </div>
</template>

<script>
import CustomInput from "./CustomInput.vue";
import CustomPhone from "./CustomPhone.vue";


export default {
  name: "HelloWorld",
  components: {
    CustomInput,
    CustomPhone,
  },
  data() {
    return {
      text: '',
      email: '',
      phone: '',
    };
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.row {
  text-align: left;
  margin-bottom: 20px;
}
label,
input{
  display: block;
}
input {
  border: 1px solid #ced4da;
  border-radius: 0.25rem;
  height: 2rem;
  padding: 0rem 0.6rem;
  font-size: 1rem;
}
</style>
