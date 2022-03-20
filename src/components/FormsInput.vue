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
           <lable> Select User Role </lable>

          <select v-model="role" class="form-control">
            <option value="Web Designer">Web Designer</option>
            <option value="Mainframe Developer">Mainframe Developer</option>
            <option value="Business Analyst">Business Analyst</option>
          </select>
                   <br />

        <div class="mb-3 form-check" >
          <input type="radio" class="form-check-input" name="exampleCheck" value="Male" v-model="gender"/>
          <label class="form-check-label">Male</label>
            <br/>
         <input type="radio" class="form-check-input" name="exampleCheck" value="FeMale" v-model="gender"/>
          <label class="form-check-label" >
            FeMale</label>

          <br />
        </div>

                       <br />

        <div class="mb-3 form-check" >
          <input type="checkbox" class="form-check-input"  value="Physics" v-model="subjects"/>
          <label class="form-check-label">Physics</label>
            <br/>
         <input type="checkbox" class="form-check-input"  value="Chemistry" v-model="subjects"/>
          <label class="form-check-label" > Chemistry  </label>
          <br />
         <input type="checkbox" class="form-check-input"  value="Maths" v-model="subjects"/>
          <label class="form-check-label" > Maths  </label>
          <br />

        </div>
 
        <button type="submit" @click="setoutput" class="btn btn-primary">
          Submit
        </button>
      </form>
        <br />
        
    <!-- <div v-if="showOutput"> -->
    <p class="bg-warning">Email ID Entered :{{ emailInput }}</p>
    <p class="bg-warning">Password Entered :{{ passwordInput }}</p>
    <p class="bg-warning">Role selected :{{ role }}</p>
   <p class="bg-warning">Gender :{{ gender}}</p>
   <p class="bg-warning">Subjectes :{{ subjects.join('-') }}</p>

    </div>

    <!-- </div> -->
  </div>
</template>

<script>
export default {
  data() {
    return {
      emailInput: "",
      passwordInput: "",
      showOutput: false,
      role: "",
      gender:'Male',
      subjects:[]
    };
  },
  methods: {
    setoutput() {
      this.showOutput = true;
    },

    formSubmit(event) {
      console.log(event);
      // event.preventDefault();
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
  height: 100%;
  border: 3px double rebeccapurple;
  margin: auto;
  background: white;
  text-align: left;
  padding: 40px;
  border-radius: 10px;
}
</style>