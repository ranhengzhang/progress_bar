<template>
    <div class="box">
        <div class="progress">
            <div class="bar" ref="bar" :style="`width: ${scale}`"></div>
            <div class="button" :style="`left: calc(${scale} - 24px)`">
                <slot>
                    <img src="@/assets/progress_bar_button.png" alt="">
                </slot>
            </div>
        </div>
        <div class="title">{{ title }}的进度：{{ recent }}/{{ total }}</div>
    </div>
</template>

<script setup>
import {defineProps, onMounted, ref} from "vue";

const props = defineProps(['title', 'total', 'recent', 'colors']);

const scale = (props.recent / props.total * 100).toFixed(2) + '%'

const bar = ref(null);
const colors = props.colors || ['#c0c5f3', '#9379e2', '#4b3a97']
onMounted(()=>{
    bar.value.style.backgroundImage = `linear-gradient(${colors.join(', ')})`
})

</script>

<style lang="less" scoped>
.box {
    width: 600px;
    margin: 20px auto;

    .progress {
        position: relative;
        height: 24px;
        border-radius: 12px;
        background-color: #eee;
        border: #ddd solid 2px;

        .bar {
            height: 100%;
            border-radius: inherit;
        }

        .button {
            width: 48px;
            height: 48px;
            position: absolute;
            top: -16px;
            border-radius: 50%;
            border: #ccc 2px solid;
            background-color: #bbb;
            overflow: hidden;

            img {
                width: 100%;
                height: 100%;
            }
        }
    }

    .title {
        text-align: center;
        margin-top: 8px;
    }
}
</style>
