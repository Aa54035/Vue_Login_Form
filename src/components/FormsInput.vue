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
          <div v-if="showPasswordError">{{ this.message }}</div>
        </div>
        <lable> Select User Role </lable>

        <select v-model="role" class="form-control">
          <option value="Web Designer">Web Designer</option>
          <option value="Mainframe Developer">Mainframe Developer</option>
          <option value="Business Analyst">Business Analyst</option>
        </select>
        <br />

        <lable> Enter your Skills </lable>
        <button @click="clearSkills">clear</button>

        <input
          type="text"
          class="form-control"
          v-model="tempSkills"
          @keyup.alt="addSkills"
        />
        <br />
        <!-- <h3>    {{this.skills.join(',')}}</h3> -->
        <div v-for="items in skills" :key="items" class="pills">
          <span @click="removeskills(items)"> {{ items }} </span>
        </div>

        <div class="mb-3 form-check">
          <input
            type="radio"
            class="form-check-input"
            name="exampleCheck"
            value="Male"
            v-model="gender"
          />
          <label class="form-check-label">Male</label>
          <br />
          <input
            type="radio"
            class="form-check-input"
            name="exampleCheck"
            value="FeMale"
            v-model="gender"
          />
          <label class="form-check-label"> FeMale</label>

          <br />
        </div>

        <br />

        <div class="mb-3 form-check">
          <input
            type="checkbox"
            class="form-check-input"
            value="Physics"
            v-model="subjects"
          />
          <label class="form-check-label">Physics</label>
          <br />
          <input
            type="checkbox"
            class="form-check-input"
            value="Chemistry"
            v-model="subjects"
          />
          <label class="form-check-label"> Chemistry </label>
          <br />
          <input
            type="checkbox"
            class="form-check-input"
            value="Maths"
            v-model="subjects"
          />
          <label class="form-check-label"> Maths </label>
          <br />
        </div>

        <div class="buttonclass">
          <button type="submit" @click="setoutput" class="btn btn-primary">
            Create Account
          </button>
        </div>
      </form>
      <br />

      <!-- <div v-if="showOutput"> -->
      <p class="bg-warning">Email ID Entered :{{ emailInput }}</p>
      <p class="bg-warning">Password Entered :{{ passwordInput }}</p>
      <p class="bg-warning">Role selected :{{ role }}</p>
      <p class="bg-warning">Gender :{{ gender }}</p>
      <p class="bg-warning">Subjectes :{{ subjects.join("-") }}</p>
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
      gender: "Male",
      subjects: [],
      tempSkills: "",
      skills: [""],
      message: "",
      showPasswordError: false,
    };
  },
  methods: {
    removeskills(singleSkill) {
      this.skills = this.skills.filter((e) => singleSkill != e);
    },

    clearSkills() {
      this.skills.length = 0;
      this.tempSkills = "";
    },
    addSkills(event) {
      if (event.key === ",") {
        if (!this.skills.includes(this.tempSkills)) {
          console.log(" " + this.skills.join(","));
          this.skills.push(this.tempSkills);
          this.tempSkills = "";
        }
      }
    },

    formSubmit(event) {
      console.log(event);
      // event.preventDefault();
    },
    setoutput() {
      let strongPassword = RegExp(
        "(?=.*[a-z])(?=.*[A-Z])(?=.*[0-9])(?=.*[^A-Za-z0-9])(?=.{8,})"
      );
      // let mediumPassword = RegExp('((?=.*[a-z])(?=.*[A-Z])(?=.*[0-9])(?=.*[^A-Za-z0-9])(?=.{6,}))|((?=.*[a-z])(?=.*[A-Z])(?=.*[^A-Za-z0-9])(?=.{8,}))')

      if (strongPassword.test(this.passwordInput)) {
        this.showPasswordError = false;
        this.message = " " + this.passwordInput + " is correct Email  ";
      } else {
        this.showPasswordError = true;
        this.message = " " + this.passwordInput + " is not correct ";
      }
      if (!this.showPasswordError) {
        console.log("Email address is :" + this.emailInput);
        console.log("password is :" + this.passwordInput);
        console.log("Gender  is :" + this.gender);
        console.log("subjects are :" + this.subjects.join(","));
        console.log("skills are " + this.skills.join(","));
      }
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
.pills {
  display: inline-block;
  margin: 20px 10px 0 0;
  padding: 6px 12px;
  border-radius: 20px;
  letter-spacing: 2px;
  cursor: pointer;
  font-weight: bold;
  color: bisque;
  background-color: aquamarine;
}
.buttonclass {
  text-align: center;
}
.btn-primary {
  border: 2px;
  margin-top: 20px;
  padding: 10px 20px;
  color: white;
  background: rgb(67, 244, 250);
  border-radius: 20px;
}
</style>