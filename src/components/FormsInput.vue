<template>
  <div class="block">
    <h4>Employee Form Submitton</h4>
    <div class="form-group">
      <form @submit.prevent="formSubmit">
        <div class="mb-3">
          <label for="exampleInputEmail1" class="form-label"
            >Email address</label
          >
          <input
            type="email"
            class="form-control"
            id="exampleInputEmail1"
            aria-describedby="emailHelp"
            v-model="emailInput"
          />
        </div>
        <div class="mb-3">
          <label for="exampleInputPassword1" class="form-label">Password</label>
          <input
            type="password"
            class="form-control"
            id="exampleInputPassword1"
            v-model="passwordInput"
          />
        </div>
        <div class="mb-3 form-check">
          <input type="checkbox" class="form-check-input" id="exampleCheck1" />
          <label class="form-check-label" for="exampleCheck1"
            >Check me out</label
          >
        </div>
        <button type="submit" @click="setoutput" class="btn btn-primary">
          Submit
        </button>
      </form>
    </div>
    <div v-if="showOutput">
      <p class="bg-primary">Email ID Entered :{{ emailInput }}</p>
      <p class="bg-primary">Password Entered :{{ passwordInput }}</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      emailInput: "",
      passwordInput: "",
      showOutput: false,
    };
  },
  methods: {
    setoutput() {
      this.showOutput = true;
    },

    formSubmit(event) {
      event.preventDefault();
    },
  },
};
</script>

<style>
.block {
  width: 600px;
  border-radius: 20px;
  background: yellowgreen;
  color: rgb(25, 33, 41);
  text-align: center;
  padding: 100px 0;
  margin: 40px auto;

  border: 5px solid black;
  font-family: Arial, Helvetica, sans-serif;
  text-decoration: underline;
}
.form-group {
  width: 400px;
  height: 300px;
  border: 3px double rebeccapurple;
  margin: auto;
  background: white;
  text-align: left;
  padding: 40px;
  border-radius: 10px;
}
</style>