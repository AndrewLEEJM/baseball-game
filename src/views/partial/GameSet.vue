<template>
  <div class="computer right">
    <h2>덤벼라 휴먼</h2>
    <img
      src="@/assets/robot.jpg"
      alt=""
    >
  </div>
</template>

<script>
export default {
  name: 'GameSet',
  data() {
    return {
      result: 0,
    };
  },
  created() {
    let num1 = Math.floor(Math.random() * 10);
    if (num1 === 0) {
      num1 = 1;
    }
    let num2 = 0;
    let num3 = 0;
    // eslint-disable-next-line no-constant-condition
    while (true) {
      num2 = Math.floor(Math.random() * 10);
      num3 = Math.floor(Math.random() * 10);
      if (num1 !== num2 && num1 !== num3 && num2 !== num3) {
        break;
      }
    }
    this.result = (num1 * 100) + (num2 * 10) + num3;
    this.$emit('setting-number', this.result);
  },
};
</script>
