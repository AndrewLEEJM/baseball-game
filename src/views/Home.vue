<template>
  <div class="home">
    <h1>야구 게임</h1>
    <div class="main-container">
      <result-section @check-result="compareResult" />
      <game-set @setting-number="settingNumber" />
    </div>
  </div>
</template>

<script>
import GameSet from './partial/GameSet.vue';
import ResultSection from './partial/ResultSection.vue';

export default {
  name: 'Home',
  components: {
    GameSet,
    ResultSection,
  },
  data() {
    return {
      result: 0,
    };
  },
  methods: {
    compareResult(val) {
      if (this.result === val) {
        console.log('정답!');
      }

      const r = this.result.toString().split('');
      const inputVal = val.toString().split('');
      let strike = 0;
      let ball = 0;
      /* if (inputVal[0] === r[0]) {
        strike++;
      }
      if (inputVal[1] === r[1]) {
        strike++;
      }
      if (inputVal[2] === r[2]) {
        strike++;
      } */
      inputVal.forEach((n, idx) => {
        if (n === r[idx]) {
          strike++;
        }
      });
      inputVal.forEach((n, idx1) => {
        r.forEach((m, idx2) => {
          if (idx1 !== idx2) {
            if (n === m) {
              ball++;
            }
          }
        });
      });
      if (strike === 0 && ball === 0) {
        console.log('out!!!');
        return;
      }

      /*    if (inputVal[0] === r[1]) {
        ball++;
      }
      if (inputVal[0] === r[2]) {
        ball++;
      }
      if (inputVal[1] === r[2]) {
        ball++;
      }
      if (inputVal[1] === r[0]) {
        ball++;
      }
      if (inputVal[2] === r[0]) {
        ball++;
      }
      if (inputVal[2] === r[1]) {
        ball++;
      } */
      console.log(`입력값: ${val}, ${strike} Strike! ${ball} Ball!`);
    },
    settingNumber(val) {
      this.result = val;
    },
  },
};
</script>
