<template>
  <div id="userLoginView">
    <h2 style="margin-bottom: 16px">用户登录</h2>
    <a-form
        :model="form"
        auto-label-width
        label-align="left"
        style="max-width: 480px; margin: 0 auto"
        @submit="handleSubmit"
    >
      <a-form-item field="userAccount" label="账号">
        <a-input v-model="form.userAccount" placeholder="请输入账号" />
      </a-form-item>
      <a-form-item field="userPassword" label="密码" tooltip="密码不少于 8 位">
        <a-input-password
            v-model="form.userPassword"
            placeholder="请输入密码"
        />
      </a-form-item>
      <a-form-item
          field="checkPassword"
          label="确认密码"
          tooltip="密码不少于 8 位"
      >
        <a-input-password
            v-model="form.checkPassword"
            placeholder="请输入确认密码"
        />
      </a-form-item>
      <a-form-item>
        <a-button
            html-type="submit"
            style="width: 120px; margin-right: 50px"
            type="primary"
        >
          注册
        </a-button>
      </a-form-item>
    </a-form>
  </div>
</template>

<script lang="ts" setup>
import { reactive } from "vue";
import { UserControllerService, UserLoginRequest } from "../../../generated";
import message from "@arco-design/web-vue/es/message";
import { useRouter } from "vue-router";

/**
 * 表单信息
 */
const form = reactive({
  userAccount: "",
  userPassword: "",
} as UserLoginRequest);

const router = useRouter();

/**
 * 提交表单
 * @param data
 */
const handleSubmit = async () => {
  const res = await UserControllerService.userRegisterUsingPost(form);
  // 注册成功，跳转到登录页
  if (res.code === 0) {
    router.push({
      path: "/user/login",
      replace: true,
    });
  } else {
    message.error("注册失败，" + res.message);
  }
};
</script>
