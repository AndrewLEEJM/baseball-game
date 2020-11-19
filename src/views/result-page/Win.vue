<template>
  <div class="about">
    <img
      src="@/assets/homerun.gif"
      alt=""
    >
    <br>
    <button @click="$router.push('/')">
      돌아가기
    </button>
  </div>
</template>
<style  scoped>
.about{
  margin-top: 100px;
  text-align: center;
}
</style>
