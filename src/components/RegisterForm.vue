<template>
  <div class="card-back">
    <div class="center-wrap">
      <form @submit.prevent="register" class="section text-center">
        <h4 class="mb-4 pb-3">ثبت نام</h4>
        <div class="row">
          <div class="col-md-6">
            <div class="form-group">
              <input
                type="text"
                name="logname"
                class="form-style"
                placeholder="نام و نام خانوادگی"
                id="logname"
                autocomplete="off"
                v-model="name"
              />
              <i class="input-icon uil uil-user"></i>
            </div>
          </div>
          <div class="col-md-6">
            <div class="form-group">
              <input
                type="email"
                class="form-style"
                placeholder="ایمیل خود را وارد کنید"
                autocomplete="off"
                v-model="email"
              />
              <i class="input-icon uil uil-at"></i>
            </div>
          </div>
          <div class="col-md-6">
            <div class="form-group mt-2">
              <input
                type="password"
                name="password"
                class="form-style"
                placeholder="کلمه عبور"
                id="password"
                autocomplete="off"
                v-model="password"
              />
              <i class="input-icon uil uil-lock-alt"></i>
            </div>
          </div>
          <div class="col-md-6">
            <div class="form-group mt-2">
              <input
                type="password"
                class="form-style"
                placeholder="تکرار کلمه عبور"
                autocomplete="off"
                v-model="confirmPassword"
              />
              <i class="input-icon uil uil-lock-alt"></i>
            </div>
          </div>
          <div class="col-md-6 mt-2">
            <div class="form-group mt-2">
              <input
                type="number"
                class="form-style"
                placeholder="شماره تلفن"
                autocomplete="off"
                v-model="phoneNumber"
              />
              <i class="input-icon uil uil-phone"></i>
            </div>
          </div>
          <div class="col-md-6 mt-4 text-center">
            <div class="form-group">
              <label for="1">نامشخص</label>
              <input
                class="m-2"
                type="radio"
                id="1"
                value="نامشخص"
                name="gender"
                v-model="gender"
              />

              <label for="2">آقا</label>
              <input
                class="m-2"
                type="radio"
                id="2"
                value="آقا"
                name="gender"
                v-model="gender"
              />

              <label for="3">خانم</label>
              <input
                class="m-2"
                type="radio"
                id="3"
                value="خانم"
                name="gender"
                v-model="gender"
              />
            </div>
          </div>
        </div>
        <button class="btn mt-4" type="submit">ثبت نام</button>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: "RegisterForm",
  data() {
    return {
      name: "",
      email: "",
      password: "",
      confirmPassword: "",
      gender: "نامشخص",
      phoneNumber: "",
    };
  },
  methods: {
    register() {
      console.log(
        `name : ${this.name} , email : ${this.email} ,password : ${this.password} , confirmPassword : ${this.confirmPassword} , phoneNumber : ${this.phoneNumber} , gender : ${this.gender}`
      );
    },
  },
};
</script>
