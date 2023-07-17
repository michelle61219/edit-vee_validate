<template>
  <div class="home">
    <VForm @submit="onSubmit" v-slot="{ errors, meta, resetForm }">
      <div class="mb-3">
        <label for="email" class="form-label">Email</label>
        <VField
          id="email"
          name="email"
          type="email"
          class="form-control"
          v-model="user.email"
          :class="{ 'is-invalid': errors['email'] }"
          rules="email|required"
          placeholder="請輸入 Email"
        ></VField>
        <error-message name="email" class="invalid-feedback"></error-message>
      </div>

      <div class="mb-3">
        <label for="name" class="form-label">姓名</label>
        <VField
          id="name"
          name="姓名"
          type="text"
          class="form-control"
          v-model="user.name"
          :class="{ 'is-invalid': errors['姓名'] }"
          rules="required"
          placeholder="請輸入姓名"
        ></VField>
        <error-message name="name" class="invalid-feedback"></error-message>
      </div>

      <div class="mb-3">
        <label for="phone" class="form-label">電話</label>
        <VField
          id="phone"
          name="電話"
          type="text"
          class="form-control"
          v-model="user.phone"
          :class="{ 'is-invalid': errors['電話'] }"
          :rules="isPhone"
          placeholder="請輸入電話"
        ></VField>
        <error-message name="phone" class="invalid-feedback"></error-message>
      </div>

      <div class="mb-3">
        <label for="region" class="form-label">地區</label>
        <VField
          id="name"
          name="地區"
          class="form-control"
          :class="{ 'is-invalid': errors['地區'] }"
          placeholder="請輸入地區"
          rules="required"
          v-model="user.region"
          as="select"
        >
          <option value="">請選擇地區</option>
          <option value="台北市">台北市</option>
          <option value="高雄市">高雄市</option>
        </VField>
        <error-message name="region" class="invalid-feedback"></error-message>
      </div>

      <div class="mb-3">
        <label for="address" class="form-label">地址</label>
        <VField
          id="address"
          name="地址"
          type="text"
          class="form-control"
          v-model="user.address"
          :class="{ 'is-invalid': errors['地址'] }"
          rules="required"
          placeholder="請輸入地址"
        ></VField>
        <error-message name="address" class="invalid-feedback"></error-message>
      </div>

      <button class="btn btn-primary" type="submit" :disabled="!meta.valid">
        Submit
      </button>
      <button class="btn btn-primary" type="button" @click="resetForm">
        重設
      </button>
    </VForm>
  </div>
</template>

<script>
export default {
  name: 'HomeView',
  data() {
    return {
      user: {
        email: '',
        name: '',
        address: '',
        phone: '',
      },
    }
  },
  created() {
    console.log(this)
  },
  methods: {
    onSubmit() {
      console.log(this.user)
    },
    isPhone(value) {
      const phoneNumber = /^(09)[0-9]{8}$/
      return phoneNumber.test(value) ? true : '需要正確的電話號碼'
    },
  },
}
</script>
