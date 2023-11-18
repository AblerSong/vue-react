<template>
  <div>
    <mt-field :label="model.label" :placeholder="model.placeholder" v-model="model.text" :type="model.type"></mt-field>
  </div>
</template>
<script>
export class InputCellModel {
  constructor() {
    this.text = ""
    this.label = "label"
    this.type = ""
  }
  
  get placeholder() {
    return `请输入${this.label}`
  }
}

export default {
  props: {
    model: {
      type: Object,
      validator: (value) => value instanceof InputCellModel,
      default: function () {
        return new InputCellModel()
      },
    },
  },
  name: "InputCell",
}
</script>
