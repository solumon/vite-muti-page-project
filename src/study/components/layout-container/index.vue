<template>
  <div class="b-layout-container">
    <div class="b-layout-content-border">
      <page-right-entrance
        class="b-layout-entrance"
        show-listen
        show-answer
        @answer="$emit('answer')"
        @listening="onListen"
      />
      <div class="b-layout-content">
        <div class="b-layout-area">
          <slot/>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import PageRightEntrance from './page-right-entrance.vue';
import PageTitle from './page-title.vue';

export default {
  name: 'LayoutContainer',
  components: {PageTitle, PageRightEntrance},
  props: {
    /* 有标题时是否隐藏标题 */
    hiddenTitle: {
      type: Boolean,
      default: false,
    },
    /* 如果指定了标题则使用指定的标题，默认通过vuex读取slide中的标题 */
    title: {
      type: String,
      default: '',
    },
    /* 如果指定了标题则使用指定的标题音频，默认通过vuex读取slide中的标题音频 */
    audio: {
      type: String,
      default: '',
    },
    /* 是否显示对答案按钮 */
    showAnswer: {
      type: Boolean,
      default: false,
    },
  },
  methods: {
    onListen() {

    },
  },
};
</script>

<style lang="scss" scoped>

div {
  box-sizing: border-box;
}

.b-layout-container {
  height: 100%;
  width: 100%;
  display: flex;
  justify-content: flex-start;
  align-items: stretch;

  .b-layout-content-border {
    position: relative;
    display: flex;
    align-items: stretch;
    flex: 1 0;
    height: calc(100vh - 1.24rem);
    margin: 0.2rem 0.7rem 1.04rem 0.6rem;
    background: #5CB4FF;
    box-shadow: inset 0 0 0.2rem 0 rgba(255, 255, 255, 0.5);
    border-radius: 0.4rem;

    .b-layout-content {
      display: flex;
      flex-direction: column;
      flex: 1 0;
      background: #F2F9FF url("./assets/ppt-bj@2x.png") repeat center/0.44rem 0.44rem;
      border-radius: 0.3rem;
      margin: 0.21rem;
      overflow: auto;
      padding: 0.6rem 0.4rem 0.4rem;

      .b-layout-page-title {
        flex-shrink: 0;
        margin-bottom: 0.24rem;
        align-self: flex-start;
      }

      .b-layout-area {
        display: flex;
        flex: 1 0;
        overflow: hidden;
      }
    }

    .b-layout-entrance {
      position: absolute;
      right: -0.66rem;
      bottom: 0.78rem;
      z-index: 10;
    }
  }
}
</style>
