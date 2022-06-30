<template>
  <div>
    <ul>
      <li v-for="item in navs" :key="item">{{ item }}</li>
    </ul>
    <button @click="btn">走一走</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      navs: ['帅哥', '程序员', '美女'],
    };
  },
  methods: {
    btn() {
      this.navs.push(this.navs[0]);
      this.navs.shift();
    },
  },
};
</script>

<style></style>
