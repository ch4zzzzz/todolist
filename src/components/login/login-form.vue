<template>
  <div class="panel panel-default">
    <form class="login-form">
      <h3>Your to-do list!</h3>
      <img class="login-img img-responsive" src="./img/login.jpg" alt="123">
      <!-- {% csrf_token %} -->
      <div class="form-group">
        <label for="username">username</label>
        <input type="text" name="username" class="form-control" id="username">
      </div>
      <div class="form-group">
        <label for="password">password</label>
        <input type="password" name="password" class="form-control" id="password">
      </div>
      <div class="form-group input-submit">
        <button class="btn btn-default" type="submit" id="login">登录</button>
        <button class="btn btn-default" type="submit" id="sign-in">注册</button>
      </div>

    </form>
  </div>

</template>

<script>
export default {
  name: 'login-form',

}
</script>

<style scoped>

h3 {
    text-align: center;
}

.login-form {
  margin: 5rem;
  line-height: 30px;
}

.login-img {

  min-width: 150px;
  margin: 0 auto;
  text-align: center;
}
.input-submit {
  text-align: center;
}


@import "https://cdn.jsdelivr.net/npm/bootstrap@3.3.7/dist/css/bootstrap.min.css";

</style>
