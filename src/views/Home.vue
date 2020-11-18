<template>
  <div class="home">
    <h1>야구 게임</h1>
    <div class="main-container">
      <div class="gamer left">
        <input
          type="text"
          placeholder="정답을 입력해주세요."
        >
      </div>
      <game-set />
    </div>
  </div>
</template>

<script>
import GameSet from './partial/GameSet.vue';

export default {
  name: 'Home',
  components: {
    GameSet,
  },
};
</script>
