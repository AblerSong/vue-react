<template>
  <div>
    <mt-button :type="model.type" :size="model.size" @click="clickButton">{{ model.text }}</mt-button>
  </div>
</template>

<script>
import { ButtonCellModel } from "./model"
export default {
  props: {
    model: {
      type: Object,
      validator: (value) => value instanceof ButtonCellModel,
      default: function () {
        return new ButtonCellModel()
      },
    },
  },
  name: "ButtonCell",
  methods: {
    clickButton() {
      this.model.clickFn()
    },
  },
}
</script>
