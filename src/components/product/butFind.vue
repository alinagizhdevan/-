<template>
  <div class="col find">
    <input type="button" value="Find" id="findBtn" class="btn" @click="sendResultData">
  </div>
</template>

<script>
export default {
  name: "butFind.vue",
  data: () => ({
    resultData: {},
  }),
  props: {
    productType: {
      type: String,
      default: '',
    },
    inputData: {
      type: String,
      default: '',
    }
  },
  methods: {
    getWords(str) {
      return str.replace(/[,.!?:"\n]+/g, ' ')
          .match(/[a-zа-яіїєґёыъ0-9 @`']/iug)
          .join('')
          .split(' ')
          .filter((itm) => itm !== '');
    },

    getCount(array) {
      const count = [];
      for (let item of array) {
        if (count.filter((itm) => itm.word === item)
            .length === 0) {
          count.push(
              {
                word: item,
                count: array.filter((itm) => itm === item).length
              }
          );
        }
      }
      return count;
    },

    getSort(array) {
      return array.sort((a, b) => a.count - b.count);
    },

    getSortedWordsFromStr(str) {
      const words = this.getWords(str);
      const wordsCount = this.getCount(words);
      const wordsSorted = this.getSort(wordsCount);
      return wordsSorted;
    },

    tenRarest(str) {
      return this.getSortedWordsFromStr(str).slice(0, 10);
    },

    tenCommon(str) {
      return this.getSortedWordsFromStr(str).slice(-10).reverse();
    },

    resultBeautify(array) {
      return array.map( (item) => item.word ).join('\n');
    },

    sendResultData() {
      if (this.productType) {
        if (this.inputData) {
          this.resultData = ('tenRarestWords' === this.productType) ? this.tenRarest(this.inputData) :
              ('tenMostCommonWords' === this.productType) ? this.tenCommon(this.inputData) : '';
          this.$emit('sendResult', this.resultBeautify(this.resultData) );
        } else {
          alert('Input something!!!')
        }
      } else {
        alert('Choose operation type!!!');
      }
    }
  }
}
</script>

<style lang="scss" scoped>

#findBtn {
  background-color: #008CBA;
  color: white;
  padding: 0.5em 1.5em;
  font-size: 1.2em;
  transition-duration: 0.4s;
  margin-top: 10px;

  &:hover {
    background-color: white;
    color: black;
  }
}


</style>
