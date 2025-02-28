<template>
    <div class="circular-progress-bar">
        <div class="circle" :style="{
            'height': disabledMaxWidth ? '100%' : 'max(12vw, 100px)',
            'width': disabledMaxWidth ? '100%' : 'max(12vw, 100px)',
        }">
            <svg :viewBox="`0 0 ${viewBoxSize} ${viewBoxSize}`">
                <circle class="circle-bg" :cx="radius" :cy="radius" :r="radius - strokeWidth / 2" />
                <circle class="circle-progress" :cx="radius" :cy="radius" :r="radius - strokeWidth / 2"
                    :stroke-dasharray="circumference" :stroke-dashoffset="dashOffset" />
            </svg>
            <div class="percentage">
                <slot></slot>
            </div>
        </div>
    </div>
</template>
  
<script setup lang="ts">
import { ref, computed } from "vue";

const props = defineProps({
    percentage: {
        type: Number,
        required: true,
        validator: (value: number) => value >= 0 && value <= 100,
    },
    disabledMaxWidth: Boolean,
});

const strokeWidth = 5; // Width of the progress circle
const viewBoxSize = 120; // Size of the viewBox
const radius = viewBoxSize / 2;

const circumference = computed(() => 2 * Math.PI * (radius - strokeWidth / 2));
const dashOffset = computed(() => circumference.value - (props.percentage / 100) * circumference.value);
</script>
  
<style scoped lang="scss">
.circular-progress-bar {
    display: inline-block;

    .circle {
        position: relative;
        width: max(12vw, 100px);
        height: max(12vw, 100px);
        text-align: center;

        svg {
            transform: rotate(-90deg);
        }

        &-bg {
            fill: none;
            stroke: var(--circular-inner-color); // Background color
            stroke-width: 5;
        }

        &-progress {
            fill: none;
            stroke: var(--circular-filled-color); // Progress color
            stroke-width: 5;
            stroke-linecap: round;
            transition: stroke-dashoffset 0.5s;
        }

        .percentage {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
        }
    }
}
</style>
  