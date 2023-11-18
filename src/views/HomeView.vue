<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <InputCell :model="usernameModel" v-if="usernameModel" />
    <InputCell :model="passwordModel" v-if="passwordModel" />
    <ButtonCell :model="buttonModel" v-if="buttonModel" />
  </div>
</template>

<script>
// @ is an alias to /src
import InputCell, { InputCellModel } from "@/components/InputCell"
import ButtonCell from "@/components/ButtonCell"
import { ButtonCellModel } from "@/components/ButtonCell/model"
import { Toast } from "mint-ui"

export default {
  name: "HomeView",
  components: {
    InputCell,
    ButtonCell,
  },
  data() {
    return {
      usernameModel: new InputCellModel(),
      passwordModel: new InputCellModel(),
      buttonModel: new ButtonCellModel(),
    }
  },
  created() {
    this.initUsernameModel()
    this.initPasswordModel()
    this.initButtonModel()
  },
  methods: {
    initUsernameModel() {
      this.usernameModel.label = "用户名"
    },
    initPasswordModel() {
      this.passwordModel.label = "密码"
      this.passwordModel.type = "password"
    },
    initButtonModel() {
      this.buttonModel.clickFn = () => {
        if (!this.usernameModel.text) {
          Toast("请输入用户名")
          return
        }
        if (!this.passwordModel.text) {
          Toast("请输入密码")
          return
        }
        Toast(`用户名:${this.usernameModel.text};密码${this.passwordModel.text}`)
      }
    },
  },
}
</script>
