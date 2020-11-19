<template>
  <div class="home">
    <h1>숫자 야구 게임</h1>
    <div class="main-container">
      <div v-if="info">
        <info-box />
        <br>
        <button

          @click="startGame"
        >
          시작하기 ->
        </button>
      </div>
      <div v-if="startBtn">
        <result-section @check-result="compareResult" />
        <game-set @setting-number="settingNumber" />
        <score-board :score="score" />
      </div>
    </div>
  </div>
</template>

<script>
import GameSet from './partial/GameSet.vue';
import ResultSection from './partial/ResultSection.vue';
import ScoreBoard from './partial/ScoreBoard.vue';
import InfoBox from './partial/InfoBox.vue';

export default {
  name: 'Home',
  components: {
    GameSet,
    ResultSection,
    ScoreBoard,
    InfoBox,
  },
  data() {
    return {
      result: 0,
      life: 9,
      score: {},
      startBtn: false,
      info: true,
    };
  },
  methods: {
    compareResult(val) {
      if (this.result === val) {
        this.$router.push('/Win');
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
      this.life--;
      this.score = {
        inputVal: val,
        strike,
        ball,
      };
      if (this.life === 0) {
        this.$router.push('/Lose');
      }
    },
    settingNumber(val) {
      this.result = val;
    },
    startGame() {
      this.startBtn = true;
      this.info = false;
    },
  },
};
</script>
<style>
.home{
  text-align: center;
  overflow: hidden;
}
.left, .right{
  width: 50%;
  height: 300px;
}
.right{
  float: right;
}
.right img{
  width: 70%;
}
.left{
  float: left;
}
.score{
    border: 4px solid black;
    width: 50%;
    min-height: 301px;
    clear: both;
    margin: 0 auto;
    background: rgb(95, 177, 119);
    color: honeydew;
}
.main-container{
  clear: both;
  width: 60%;
  margin: 0 auto;
}
.gamer input{
  margin-top: 60px;
  border-radius: 5px;
  width: 200px;
  height: 30px;
}
.gamer button{
  border-radius: 5px;
  width: 50px;
  height: 33px;
}
.score p{
  font-size: 1.3em;
}
.info{
  border: 1px solid black;
  background: azure;
}
</style>
