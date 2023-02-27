<template>
    <div class="page-right-entrance">
        <div
            v-show="showListen"
            class="listening"
            @click="$emit('listening')"
        />
        <div
            :class="{'answer-all': true, 'is-hidden': !showAnswer}"
            @click="$emit('answer')"
        >
            <span>答案</span>
        </div>
    </div>
</template>

<script>
export default {
    name: 'PageRightEntrance',
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
.page-right-entrance {
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
    align-items: flex-start;
    min-width: 1.2rem;

    .listening {
        cursor: pointer;
        width: 1.2rem;
        height: 0.78rem;
        background: url("./assets/listening.png") no-repeat center/cover;
    }

    .answer-all {
        box-sizing: border-box;
        cursor: pointer;
        width: 0.8rem;
        height: 1rem;
        background: url("./assets/answering.png") no-repeat center/cover;
        margin-top: 0.6rem;
        margin-left: 0.32rem;
        display: flex;
        justify-content: center;
        align-items: center;

        &.is-hidden {
            visibility: hidden;
        }

        & > span {
            display: inline-block;
            font-size: 0.32rem;
            color: #FFF;
            font-weight: bold;
            width: 0.45rem;
            line-height: 0.43rem;
        }
    }
}
</style>
