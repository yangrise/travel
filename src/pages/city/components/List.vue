<template>
  <div class="list" ref="wrapper">
    <div>
      <div class="area">
        <div class="title border-topbottom">当前城市</div>
        <div class="button-list">
          <div class="button-wrapper">
            <div class="button">{{this.currenCity}}</div>
          </div>
        </div>
      </div>
      <div class="area">
        <div class="title border-topbottom">热门城市</div>
        <div class="button-list">
          <div class="button-wrapper"
            v-for="item of hot"
            :key="item.id"
            @click="handleCityClick(item.name)"
            >
            <div class="button">{{item.name}}</div>
          </div>
        </div>
      </div>
      <div class="area" v-for="(item, key) of cities" :key="key" :ref="key">
        <div class="title border-topbottom">{{key}}</div>
        <div class="item-list">
          <div class="item border-bottom" v-for="innerItem of item" :key="innerItem.id"
          @click="handleCityClick(innerItem.name)"
          >{{innerItem.name}}</div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import { mapState, mapMutations } from 'vuex'
import Bscroll from 'better-scroll'
export default {
  name: 'CityList',
  mounted () {
    this.scroll = new Bscroll(this.$refs.wrapper)
  },
  methods: {
    handleCityClick (city) {
      // this.$store.dispatch('changeCity', city)
      // this.$store.commit('changeCity', city)
      this.changeCity(city)
      this.$router.push('/')
    },
    ...mapMutations(['changeCity'])// 将vuex中的方法映射到方法中
  },
  computed: {
    ...mapState({
      currenCity: 'city'
    })// 把vuex中的属性映射到计算属性中
  },
  props: {
    cities: Object,
    hot: Array,
    letter: String
  },
  watch: {
    letter () {
      if (this.letter) {
        const element = this.$refs[this.letter][0]
        this.scroll.scrollToElement(element)
      }
    }
  }
}
</script>
<style lang="stylus" scoped>
  @import "~styles/varibles.styl";
  .border-topbottom
    &:before
      background-color #ccc
    &:after
      background-color #ccc
  .border-bottom
    &:before
      background-color #ccc
  .list
    position absolute
    top 1.58rem
    left 0
    right 0
    bottom 0
    overflow hidden
    .title
      line-height .54rem
      background #eeeeee
      padding-left .2rem
      color #666
      font-size .26rem
    .button-list
      padding 0.1rem .6rem .1rem .1rem
      overflow hidden
      .button-wrapper
        float left
        width 33.33%
        .button
          text-align  center
          margin .1rem
          border .02rem solid #ccc
          padding 0.1rem 0
          border-radius .06rem
    .item-list
      .item
        line-height 0.76rem
        color #666
        padding-left .2rem
</style>
