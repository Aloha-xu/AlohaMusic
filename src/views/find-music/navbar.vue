<template>
  <div class="nav-bar" >
    <div
      v-for="(item, index) in findMusictype"
      :key="index"
      class="nav-bar-item"
      :class="currentIndex === index ? 'active' : ''"
      @click="itemClick(index)"
    >
      {{ item }}
    </div>
  </div>
</template>

<script>
export default {
  name: "NavBar",
  data() {
    return {
      findMusictype: ["推荐", "歌单", "主播电台", "排行榜", "歌手", "最新音乐"],
    };
  },
  methods: {
    itemClick(index) {
      switch (index) {
        case 0:
          this.$router.push("/recommend");
          break;
        case 1:
          this.$router.push("/songlist");
          break;
        case 2:
          this.$router.push("/anchorradio");
          break;
        case 3:
          this.$router.push("/rank");
          break;
        case 4:
          this.$router.push("/singer");
          break;
        case 5:
          this.$router.push("/newmusic");
          break;
      }
      this.$store.commit("refeshCurrentNavIndex", index);
    },
  },
  created() {
    this.itemClick(this.currentIndex);
  },
  computed: {
    currentIndex() {
      return this.$store.state.navCurrentIndex;
    },
  },
};
</script>

<style scoped lang="scss">
@import "@/assets/css/base.scss";
.nav-bar {
  display: flex;
  position: relative;
  width: 100%;
  text-align: center;
  color: black;
  line-height: 45px;
  font-size: 15px;
  padding: 8px 0px 10px 15px;
  .nav-bar-item {
    width: 80px;
    cursor: pointer;
  }
  .active {
    border-bottom: 2px solid $theme-color;
    font-size: 17px;
    font-weight: 900;
  }
}


</style>