<template>
    <div class="page-content">
        <div class="wrapper">
            <slot />
        </div>
        <slot name="right-entrance">
            <page-right-entrance
                class="side-module"
                :show-listen="showListen"
                :show-answer="showAnswer"
                @listening="$emit('listening')"
                @answer="$emit('answer')"
            />
        </slot>
    </div>
</template>

<script>
import PageRightEntrance from './page-right-entrance.vue';

export default {
    name: 'PageContent',
    components: { PageRightEntrance },
    props: {
        showListen: {
            type: Boolean,
            default: false,
        },
        showAnswer: {
            type: Boolean,
            default: false,
        },
    },
};
</script>

<style lang="scss" scoped>
div {
    box-sizing: border-box;
}

.page-content {
    position: relative;
    min-width: 15rem;
    min-height: 5rem;
    background: #F7FBFF;
    border-radius: 0.12rem;
    border: 0.08rem solid #94C8FF;
    box-shadow: inset 0 -0.02rem 0.06rem 0 #1788FF;

    .side-module {
        position: absolute;
        right: -0.88rem;
        bottom: 0.6rem;
        z-index: 10;
    }

    .wrapper {
        position: absolute;
        left: 0;
        right: 0;
        bottom: 0;
        top: 0;
        margin: 0.32rem 0.1rem 0.32rem 0.32rem;
        padding: 0 0.3rem;
        overflow: auto;

        &::-webkit-scrollbar {
            width: 0.36rem !important;
        }

        &::-webkit-scrollbar-button {
            display: block;
            background: #FFF;
            padding: 0;
            margin: 0;
            height: 0;
        }

        &::-webkit-scrollbar-track {
            background: #FFF;
            padding: 0;
            margin: 0;
        }

        &::-webkit-scrollbar-track-piece {
            background: #FFF;
            padding: 0;
            margin: 0;
        }

        &::-webkit-scrollbar-thumb {
            border-radius: 0.08rem;
            box-shadow: inset 0 0 0 0.02rem #59B2FE;
            background: #FFF url('../../images/scroll-bar/scroll-thumb.png') no-repeat center;
            cursor: pointer;
            padding: 0;
            margin: 0;
        }

        &::-webkit-scrollbar-button:corner-present {
            height: 0;
            padding: 0;
            margin: 0;
        }

        &::-webkit-scrollbar-button:vertical:single-button:start {
            width: 0.36rem;
            height: 0.32rem;
            background: url('../../images/scroll-bar/scroll-arrow-top.png') no-repeat;
            cursor: pointer;
            background-size: contain;
        }

        &::-webkit-scrollbar-button:vertical:single-button:end {
            width: 0.36rem;
            height: 0.36rem;
            background: url('../../images/scroll-bar/scroll-arrow-down.png') no-repeat;
            cursor: pointer;
            background-size: contain;
        }
    }
}
</style>
