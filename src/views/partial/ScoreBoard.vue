<template>
  <div class="score">
    <h2>점수판</h2>

    <div>
      <p
        v-for="(sc, idx) in scoreGroup"
        :key="idx"
      >
        | {{ idx + 1 }}회차 공격! <b>{{ sc.inputVal }}::
          {{ sc.strike }} Strike!! {{ sc.ball }} Ball!!</b> |
      </p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ScoreBoard',
  props: {
    score: {
      type: Object,
      default: () => {},
    },
  },
  data() {
    return {
      scoreGroup: [],
      // onScoreBoard: false,
    };
  },
  computed: {

  },
  watch: {
    score() {
      this.scoreGroup.push(this.score);
      // this.onScoreBoard = true;
    },
  },
  methods: {
  },
};
</script>

<style>

</style>
