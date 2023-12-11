<template>
  <div class="card-back">
    <div class="center-wrap">
      <Form
        @submit="register"
        class="section text-center"
        :validation-schema="schema"
      >
        <h4 class="mb-4 pb-3">ثبت نام</h4>
        <div class="row">
          <div class="col-md-6">
            <div class="form-group">
              <Field
                name="name"
                type="text"
                class="form-style"
                placeholder="نام و نام خانوادگی"
                id="logname"
                autocomplete="off"
                validate-on-input="true"
              />
              <i class="input-icon uil uil-user"></i>
            </div>
            <ErrorMessage name="name" />
          </div>
          <div class="col-md-6">
            <div class="form-group">
              <Field
                name="email"
                class="form-style"
                placeholder="ایمیل خود را وارد کنید"
                autocomplete="off"
                validate-on-input="true"
              />
              <i class="input-icon uil uil-at"></i>
            </div>
            <ErrorMessage name="email" />
          </div>
          <div class="col-md-6">
            <div class="form-group mt-2">
              <Field
                type="password"
                name="password"
                class="form-style"
                placeholder="کلمه عبور"
                autocomplete="off"
                validate-on-input="true"
              />
              <i class="input-icon uil uil-lock-alt"></i>
            </div>
            <ErrorMessage name="password" />
          </div>
          <div class="col-md-6">
            <div class="form-group mt-2">
              <Field
                type="password"
                name="confirmPassword"
                class="form-style"
                placeholder="تکرار کلمه عبور"
                autocomplete="off"
                validate-on-input="true"
              />
              <i class="input-icon uil uil-lock-alt"></i>
            </div>
            <ErrorMessage name="confirmPassword" />
          </div>
          <div class="col-md-6 mt-2">
            <div class="form-group mt-2">
              <Field
                type="number"
                class="form-style"
                placeholder="شماره تلفن"
                autocomplete="off"
                name="phoneNumber"
                validate-on-input="true"
              />
              <i class="input-icon uil uil-phone"></i>
            </div>
            <ErrorMessage name="phoneNumber" />
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
      </Form>
    </div>
  </div>
</template>

<script>
import { Form, Field, ErrorMessage } from "vee-validate";
import * as Yup from "yup";
export default {
  name: "RegisterForm",
  components: {
    Form,
    Field,
    ErrorMessage,
  },
  data() {
    const schema = Yup.object({
      name: Yup.string().required("نام و نام خانوادگی را وارد کنید."),
      email: Yup.string()
        .email("ایمیل وارد شده معتبر نمی باشد.")
        .required("لطفا ایمیل را وارد کنید."),
      password: Yup.string()
        .required("وارد کردن پسورد الزامی است.")
        .min(4, "پسورد باید حداقل 4 کاراکتر باشد.")
        .max(20, "پسورد نمی تواند بیشتر از 20 کاراکتر باشد."),
      confirmPassword: Yup.string()
        .oneOf([Yup.ref("password"), null], "تایید پسورد صحیح نمی‌باشد")
        .required("تایید پسورد الزامی است"),
      phoneNumber: Yup.string()
        .required("لطفا شماره موبایل را وارد کنید.")
        .length(11, "شماره تلفن نامعتبر است."),
    });
    return {
      schema,
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
