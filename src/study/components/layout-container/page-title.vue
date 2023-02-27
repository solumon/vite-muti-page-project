<template>
    <div
        :class="{
            'page-title': true,
            'point': audio
        }"
        @click.stop="titleClickEvent"
    >
        <div class="icon">
            <div class="block" />
            <div class="block" />
        </div>
        <div
            v-if="title"
            class="text"
        >
            {{ title }}
            <span
                v-show="audio"
                :class="{
                    's-title-audio-end': true,
                    [state] :true,
                }"
            />
        </div>
        <audio
            v-if="audio"
            ref="audio"
            :src="audio"
            style="display: none;"
            @ended="onEnded"
            @play="onPlay"
            @pause="onPause"
        />
    </div>
</template>

<script>
export default {
    name: 'PageTitle',
    props: {
        title: {
            type: String,
            default: '',
        },
        audio: {
            type: String,
            default: '',
        },
    },
    data() {
        return {
            state: 'stop',
        };
    },
    methods: {
        stop() {
            if (this.$refs.audio) {
                this.$refs.audio.pause();
                this.$refs.audio.currentTime = 0;
            }
        },
        onEnded() {
            this.state = 'stop';
            if (this.$refs.audio) {
                this.$refs.audio.currentTime = 0;
            }
        },
        onPlay() {
            this.state = 'play';
        },
        onPause() {
            this.state = 'stop';
            if (this.$refs.audio) {
                this.$refs.audio.currentTime = 0;
            }
        },
        titleClickEvent() {
            if (this.$refs.audio) {
                if (this.state === 'stop') {
                    this.$refs.audio.play();
                } else {
                    this.$refs.audio.pause();
                }
            }
        },
    },
};
</script>

<style lang="scss" scoped>
.page-title {
    font-size: 0.4rem;
    color: #333;
    line-height: 0.54rem;
    display: flex;
    align-items: flex-start;

    .icon {
        box-sizing: border-box;
        margin-top: 0.05rem;
        width: 0.4rem;
        height: 0.4rem;
        margin-right: 0.15rem;
        position: relative;

        .block {
            position: absolute;
            width: 0.32rem;
            height: 0.32rem;
            border-radius: 0.05rem;
            background: #5CB4FF;
            opacity: 0.5;
        }

        .block:first-child {
            left: 0;
            top: 0;
        }

        .block:last-child {
            bottom: 0;
            right: 0;
        }
    }

    .text {
        color: #333;
        font-weight: bold;
        font-size: 0.4rem;
        line-height: 0.52rem;
    }

    .s-title-audio-end {
        display: inline-block;
        vertical-align: middle;
        width: 0.4rem;
        height: 0.4rem;
    }

    .s-title-audio-end.play {
        background: url("../../images/audio-player/play-blue.gif") no-repeat center/cover;
    }

    .s-title-audio-end.stop {
        background: url("../../images/audio-player/play-blue.png") no-repeat center/cover;
    }
}

.page-title.point {
    cursor: pointer;
}
</style>
