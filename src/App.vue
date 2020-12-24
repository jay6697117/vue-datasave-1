<template>
  <div id="app">
    <h1>custom:{{ custom }}</h1>
    <h1>{{ module2 }}</h1>
    <hr />
    <div class="wrap">
      ----vuex自动缓存演示----{{ $store.state.user.name }}-------vuex自动缓存演示-------------------
      <h1>localStoreage:一直存在</h1>
      <p>{{ $store.state.custom.count }}</p>
      <button @click="increment1">+</button>
      <button @click="decrement1" style="margin-left:40px">-</button>
    </div>
    <div class="wrap">
      <h1>sessionStoreage：重启浏览器恢复原样</h1>
      <p>{{ $store.state.module2.count }}</p>

      <button @click="increment2">+</button>
      <button @click="decrement2" style="margin-left:40px">-</button>
    </div>
    <br />
  </div>
</template>

<script>
import { mapMutations } from 'vuex';

export default {
  name: 'App',
  methods: {
    ...mapMutations({
      decrement1: 'decrement1',
      increment1: 'increment1',
      increment2: 'module2/increment2',
      decrement2: 'module2/decrement2'
    })
  },
  computed: {
    custom() {
      return this.$store.state.custom;
    },
    module2() {
      return this.$store.state.module2;
    }
  },
  created() {
    console.log('this.$store.state :>> ', this.$store.state);
  }
};
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.wrap {
  text-align: center;
}
</style>
