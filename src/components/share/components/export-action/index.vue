<style lang="scss" scoped>
.export-action {
  margin-bottom: 10px;
  user-select: none;
  cursor: pointer;
  .export-action--theme {
    &.export-action--theme__yellow {
      background-image: linear-gradient(180deg, #ffeb00 0%, #ffb100 100%);
      border-color: darken(#ffb100, 10%);
      &:hover {
        background-image: linear-gradient(180deg, darken(#ffeb00, 4%) 0%, darken(#ffb100, 4%) 100%);
      }
    }
    &.export-action--theme__blue {
      background-image: linear-gradient(180deg, #61E4FF 0%, #3085FE 100%);
      border-color: darken(#3085FE, 10%);
      &:hover {
        background-image: linear-gradient(180deg, darken(#61E4FF, 4%) 0%, darken(#3085FE, 4%) 100%);
      }
    }
    &.export-action--theme__red {
      background-image: linear-gradient(180deg, #E88D37 0%, #EB2301 100%);
      border-color: darken(#EB2301, 10%);
      &:hover {
        background-image: linear-gradient(180deg, darken(#E88D37, 4%) 0%, darken(#EB2301, 4%) 100%);
      }
    }
    &.export-action--theme__violet {
      background-image: linear-gradient(180deg, #BE37E8 0%, #9701EB 100%);
      border-color: darken(#9701EB, 10%);
      &:hover {
        background-image: linear-gradient(180deg, darken(#BE37E8, 4%) 0%, darken(#9701EB, 4%) 100%);
      }
    }
    &.export-action--theme__cyan {
      background-image: linear-gradient(180deg, #37E8E3 0%, #01EB84 100%);
      border-color: #00CF76;
      &:hover {
        background-image: linear-gradient(180deg, darken(#37E8E3, 4%) 0%, darken(#01EB84, 4%) 100%);
      }
    }
  }
  .export-action--left {
    padding: 10px 0 10px 10px;
    border: 1px solid;
    border-top-left-radius: 4px;
    border-bottom-left-radius: 4px;
    img {
      width: 26px;
      height: 26px;
      margin-right: 10px;
    }
    .export-action--title {
      font-size: 12px;
      color: #FFF;
      text-shadow: 0 1px 1px rgba(0,0,0,0.40);
      background-color: rgba(#000, .3);
      border-radius: 2px;
      padding: 0 5px;
    }
    .export-action--desc {
      font-size: 10px;
      color: #FFF;
      text-shadow: 0 1px 1px rgba(0,0,0,0.40);
    }
  }
  .export-action--right {
    border: 1px solid;
    border-left: none;
    border-top-right-radius: 4px;
    border-bottom-right-radius: 4px;
    width: 55px;
    color: #FFF;
    text-shadow: 0 1px 1px rgba(0,0,0,0.40);
    font-size: 14px;
  }
}
</style>

<template>
  <div
    class="export-action"
    flex="box:last">
    <div
      class="export-action--left export-action--theme"
      :class="`export-action--theme__${color}`"
      flex="cross:center"
      @click="e => $emit('click', e)">
      <img :src="image" draggable="false">
      <div>
        <div class="export-action--title">
          {{ title }}
        </div>
        <div class="export-action--desc">
          {{ desc }}
        </div>
      </div>
    </div>
    <div
      class="export-action--right export-action--theme"
      :class="`export-action--theme__${color}`"
      flex="dir:top main:center cross:center"
      @click="$router.push({
        name: 'setting',
        query: { anchor }
      })">
      <span>设置</span>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    icon: { type: String, default: '', required: false },
    color: { type: String, default: '', required: false },
    title: { type: String, default: '', required: false },
    desc: { type: String, default: '', required: false },
    anchor: { type: String, default: '', required: false }
  },
  computed: {
    image () {
      return require(`@/assets/icon/export/${this.icon}.png`)
    }
  }
}
</script>
