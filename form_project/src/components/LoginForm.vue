<template>
  <div class="container">
    <div class="row mt-3">
      <div class="row sm-4">
        <form id="app" @submit.prevent="loginFormSubmit">
          <div class="form-group">
            <label for="username">User Name</label>
            <input
              type="text"
              name="username"
              id="username"
              placeholder="Enter your username"
              class="form-control"
              v-model="username"
            />
          </div>
          <div class="form-group">
            <label for="password">Password</label>
            <input
              type="password"
              name="password"
              id="password"
              placeholder="Enter your password"
              class="form-control"
              v-model="password"
            />
          </div>
          <button type="submit" class="btn btn-primary my-1">Login</button>
        </form>
      </div>
    </div>
    <div class="row mt-3">
        username:
        <span class="text-info ml-1">{{username}}</span>
    </div>
    <div class="row">
         password:
        <span class="text-warning ml-1">{{password}}</span>
    </div>  
  </div>
</template>

<script>
export default {
  name: "LoginForm",
  data() {
    return {
      username: "",
      password: "",
    };
  },
  method: {
    loginFormSubmit() {
      console.log(`$(this.username) $(this.password)`);
    },
  },
};
</script>


