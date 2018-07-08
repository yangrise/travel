<template>
  <div class="header">
      <div class="header-left">
          <div class="iconfont back-icon">&#xe624;</div>
      </div>
      <div class="header-input">
          <span class="iconfont">&#xe632;</span>
          输入城市/景点/游玩主题
      </div>
      <router-link to="/City">
        <div class="header-right">
            {{this.city}}
            <span class="iconfont arrow-icon">&#xe64a;</span>
        </div>
      </router-link>
  </div>
</template>
<script>
export default {
  name: 'HomeHeader',
  props: {
    city: String
  }
}
</script>
<style lang="stylus" scoped>
    @import '~styles/varibles.styl'
    .header
        line-height: $headerHeight
        display flex
        background $bgColor
        color #fff
        .header-left
            width: .64rem
            float: left
            .back-icon
                text-align center
                font-size .4rem
        .header-input
            flex: 1
            background #ffffff
            height 0.64rem
            margin-left 0.2rem
            border-radius .1rem
            margin-top .12rem
            color #cccccc
            line-height .64rem
            padding-left .2rem
        .header-right
            width: 1.24rem
            float: left
            text-align center
            color #fff
            .arrow-icon
                font-size .24rem
                margin-left -.04rem
</style>
