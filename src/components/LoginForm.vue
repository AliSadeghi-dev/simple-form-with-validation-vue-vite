<template>
  <div class="card-front">
    <div class="center-wrap">
      <Form
        @submit="login"
        :validation-schema="schema"
        class="section text-center"
      >
        <h4 class="mb-4 pb-3">ورود</h4>
        <div class="form-group">
          <Field
            name="email"
            type="email"
            class="form-style"
            placeholder="ایمیل خود را وارد کنید"
            autocomplete="off"
          />
          <i class="input-icon uil uil-at"></i>
        </div>
        <ErrorMessage name="email" />
        <div class="form-group mt-2">
          <Field
            name="password"
            type="password"
            class="form-style"
            placeholder="پسورد را وارد کنید"
            autocomplete="off"
          />
          <i class="input-icon uil uil-lock-alt"></i>
        </div>
        <ErrorMessage name="password" />

        <button type="submit" class="btn mt-4">ورود به سایت</button>
        <p class="mb-0 mt-4 text-center">
          <a class="link"> آیا کلمه عبور خود را فراموش کرده اید ؟ </a>
        </p>
      </Form>
    </div>
  </div>
</template>

<script>
import { Form, Field, ErrorMessage } from "vee-validate";
import * as Yup from "yup";

export default {
  name: "LoginForm",
  components: {
    Form,
    Field,
    ErrorMessage,
  },
  data() {
    const schema = Yup.object({
      email: Yup.string()
        .required("ایمیل را وارد کنید")
        .email("ایمیل نامعتبر است."),
      password: Yup.string()
        .required("وارد کردن پسورد الزامی است.")
        .min(4, "پسورد باید حداقل 4 کاراکتر باشد.")
        .max(20, "پسورد نمی تواند بیشتر از 20 کاراکتر باشد."),
    });
    return {
      schema,
    };
  },
  methods: {
    login(values) {
      // console.log(`email : ${this.email} , password : ${this.email}`);
      console.log(values);
    },
  },
};
</script>
