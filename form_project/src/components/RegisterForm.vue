<template>
  <div class="row">
    <div class="col-sm-6 mt-5 card mx-auto">
      <div class="card-body">
        <img 
          src="../assets/logo.png"
          alt="logo"
          class="login-logo"
        />
        <form @submit.prevent="onFormSubmit">
          <div class="form-group">
              <label htmlFor="username">User Name</label>
              <input
                type="text"
                :class="getInputClass('username')"
                id="username"
                name="username"
                placeholder="Enter your username"
                v-model="formElement.username.value"
                @keyup="onFormChange($event)"
                />
          </div>
          <div class="invalid-feedback">
            {{ getErrorMessage('username') }}
          </div>
          <div class="form-group">
              <label htmlFor="email">Email</label>
              <input
                type="email"
                :class="getInputClass('email')"
                id="email"
                name="email"
                placeholder="Enter your email"
                v-model="formElement.email.value"
                @keyup="onFormChange($event)"
                />
          </div>
          <div class="invalid-feedback">
            {{ getErrorMessage('email') }}
          </div>
          <div class="form-group">
              <label htmlFor="password">Password</label>
              <input
                type="password"
                :class="getInputClass('password')"
                id="password"
                name="password"
                placeholder="Enter your password"
                v-model="formElement.password.value"
                @keyup="onFormChange($event)"
                />
          </div>
          <div class="invalid-feedback">
            {{ getErrorMessage('password') }}
          </div>
          <div>
            <button
              type="submit"
              class="btn btn-primary"
              :disabled="!formValid"
            >
              Register
            </button>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "RegisterForm",
  data() {
    return {
      formElement: {
        username: {
          type: "text",
          value: "",
          validator: {
            required: true,
            minLength: 5,
            maxLength: 15,
          },
          touched: false,
          error: { status: true, message: "" },
        },
        email: {
          type: "email",
          value: "",
          validator: {
            required: true,
            pattern: "",
          },
          touched: false,
          error: { status: true, message: "" },
        },
        password: {
          type: "password",
          value: "",
          validator: {
            required: true,
            minLength: 6,
            maxLength: 15,
          },
          touched: false,
          error: { status: true, message: "" },
        },
      },
      formValid: false,
    };
  },
  methods: {
    onFormChange(event) {
      const name = event.target.name;
      const value = event.target.value;
      let updateForm = { ...this.formElement };
      updateForm[name].value = value;
      updateForm[name].touched = true;
      const validatorObject = this.checkValidator(
        name,
        value,
        updateForm[name].validator
      );
      updateForm[name].error = {
        status: validatorObject.status,
        message: validatorObject.message,
      };
      let formStatus = true;
      for (let name in updateForm) {
        if (updateForm[name].validator.required === true) {
          formStatus = formStatus && !updateForm[name].error.status;
        }
      }
      this.formValid = formStatus;
      this.formElement = updateForm;
    },
    checkValidator(value, rule) {
      let valid = true;
      let message = "";
      if (valid.trim().length === 0 && rule.required) {
        valid = false;
        message = "จำเป็นต้องกรอก";
      }
      if (value.length < rule.minLength && valid) {
        valid = false;
        message = `น้อยกว่า ${rule.maxLength} ตัวอักษร`;
      }
      if (value.length > rule.maxLength && valid) {
        valid = false;
        message = `มากกว่า ${rule.maxLength} ตัวอักษร`;
      }
      if (rule.pattern === "email" && valid) {
        const pattern = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
        valid = pattern.test(value);
        message = `รูปแบบอีเมลไม่ถูกต้อง`;
      }
      return { status: valid, message: message };
    },
    getInputClass(name) {
      const elementErrorStatus = this.formElement[name].error.status;
      if (!this.formElement[name].touched) {
        return ["form-control"];
      } else {
        return elementErrorStatus && this.formElement[name].touched
          ? ["is-invalid"]
          : ["is-valid"];
      }
    },
    getErrorMessage(name) {
      return this.formElement[name].error.message;
    },
    onFormSubmit() {
      const formData={};
      for(let name in this.formElement){
        formData[name]=this.formElement[name].value;
      }
      console.log(this.formElement);
    },
  },
};
</script>

<style >
  #login-logo{
    width: 100%;
    height: 200px;
    object-fit: cover;  
  }
  .card{
    max-width: 450px;
  }
</style>
