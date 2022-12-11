<template>
  <div class="row inputs">
    <div class="col input input__left">
      <label for="input_text" class="label_text">Input your text here</label>
      <textarea name="" id="inputText" cols="30" rows="10" class="textarea"
                v-model="inputText" @input="onInput"></textarea>
    </div>
    <div class="col input input__right">
      <label for="result_text" class="label_text">Result</label>
      <textarea name="" id="resultText" cols="30" rows="10" class="textarea"
                readonly v-model="resultText"></textarea>
    </div>
  </div>
</template>

<script>
export default {
  name: "Inputs.vue",
  data: () => ({
    inputText: '',
  }),
  props: {
    resultText: {
      type: String,
      default: '',
    }
  },
  methods: {

    onInput() {
      this.clearResultText();
      this.sendInputText();
    },

    sendInputText() {
      this.$emit('sendInput', this.inputText)
    },

    clearResultText() {
      this.$emit('clearResult')
    },
  }
}
</script>

<style scoped>

.inputs {
  width: 100%;
  margin: 10px 0 0 0;

}

.input {
  display: flex;
  flex-direction: column;
  width: 100%;
  font-size: 1.2em;

}

#inputText, #resultText {
  display: flex;
  font-size: 1em;
  resize: none;
  border-radius: 10px;
  margin: 10px 0 30px 0;
  padding: 10px;
  height: 150%;
  line-height: 1.2;

}

</style>