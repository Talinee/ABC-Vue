<template>
<div class="container">
    <div class="card">
        <a-form :form="form">
            <a-form-item
            :label-col="formItemLayout.labelCol"
            :wrapper-col="formItemLayout.wrapperCol"
            label="Email"
            >
            <a-input
                v-decorator="[
                'Email',
                { rules: [{ required: true, message: 'Please input your Email' }] },
                ]"
                placeholder="Please input your Email"
            />
            </a-form-item>
            <a-form-item
            :label-col="formItemLayout.labelCol"
            :wrapper-col="formItemLayout.wrapperCol"
            label="Password"
            >
            <a-input
                v-decorator="[
                'Password',
                { rules: [{ required: checkNick, message: 'Please input your password' }] },
                ]"
                placeholder="Please input your password"
            />
            </a-form-item>
            <a-form-item :label-col="formTailLayout.labelCol" :wrapper-col="formTailLayout.wrapperCol">
            <a-button type="primary" @click="Login">
                เข้าสู่ระบบ
            </a-button>
            </a-form-item>
        </a-form>
    </div>
  </div>
</template>

<script>
const formItemLayout = {
  labelCol: { span: 4 },
  wrapperCol: { span: 8 },
};
const formTailLayout = {
  labelCol: { span: 4 },
  wrapperCol: { span: 8, offset: 4 },
};
export default {
  data() {
    return {
      checkNick: false,
      formItemLayout,
      formTailLayout,
      form: this.$form.createForm(this, { name: 'dynamic_rule' }),
    };
  },
  methods: {
    check() {
      this.form.validateFields(err => {
        if (!err) {
          console.info('success');
        }
      });
    },
    handleChange(e) {
      this.checkNick = e.target.checked;
      this.$nextTick(() => {
        this.form.validateFields(['nickname'], { force: true });
      });
    },
  },
};
</script>
<style>
    .container{
        width: 100%;
    }
    .card{
        height: 580px;
        width: 452px;
        border-radius: 10px;
        margin: auto;
        background-color: #32394E;
        margin-top: 110px;

    }
    .ant-col-8{
        height: 40px;
        width: 395px;
    }
</style>