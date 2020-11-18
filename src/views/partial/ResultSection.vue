<template>
  <div class="gamer left">
    <input
      v-model="result"
      type="text"
      placeholder="정답을 입력해주세요."
      maxlength="3"
      @keyup.enter="checkResult"
    >
    <button @click="checkResult">
      확인
    </button>
  </div>
</template>

<script>
export default {
  name: 'ResultSection',
  data() {
    return {
      result: '',
    };
  },
  methods: {
    checkResult() {
      if (this.result.length < 3) {
        alert('3자리 수를 입력해주세요.');
        return;
      }
      const check = this.result.split('');
      if (check[0] === check[1] || check[0] === check[2] || check[1] === check[2]) {
        alert('같은 숫자를 입력하지 말아주세요!.');
        return;
      }
      this.$emit('check-result', parseInt(this.result, 10));
    },
  },
};
</script>

<style>

</style>
