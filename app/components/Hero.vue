<template>
    <div
        class="relative flex w-screen h-[90vh] flex-col items-center justify-center overflow-hidden -z-10">
        <p
            class="z-10 whitespace-pre-wrap text-center text-5xl font-medium tracking-tighter">
            POL GUASCH ROMERO
        </p>
        <small>Software Engineering & Machine Learning</small>
        
        <div
            v-if="loadTime !== null || co2Emission !== null"
            class="z-10 mt-6 flex flex-col items-center text-sm text-base-content/70">
            <div class="flex flex-col items-center gap-3 sm:flex-row sm:gap-4">
                <div
                    v-if="loadTime !== null"
                    class="flex items-center gap-3 rounded-full border border-base-300/60 bg-base-200/80 px-5 py-2 backdrop-blur-sm">
                    <span class="text-xs uppercase tracking-[0.2em] text-base-content/60">Load Time of this website</span>
                    <span class="text-base font-medium text-base-content">{{ formatTime(loadTime) }}</span>
                </div>
                <div
                    v-if="co2Emission !== null"
                    class="flex items-center gap-3 rounded-full border border-base-300/60 bg-base-200/80 px-5 py-2 backdrop-blur-sm">
                    <span class="text-xs uppercase tracking-[0.2em] text-base-content/60">CO₂ Impact of this website</span>
                    <span class="text-base font-medium text-base-content">{{ formatCo2(co2Emission) }}</span>
                </div>
            </div>
        </div>
        
        <Ripple circle-class="border-[hsl(var(--primary))] rounded-full" />
    </div>
</template>

<script setup lang="ts">
import { co2 } from '@tgwf/co2';
import { ref, onMounted } from 'vue';

const loadTime = ref<number | null>(null);
const co2Emission = ref<number | null>(null);

const co2Calculator = new co2(null);

const formatTime = (ms: number): string => {
    if (ms < 1000) return `${ms}ms`;
    return `${(ms / 1000).toFixed(2)}s`;
};

const formatCo2 = (grams: number): string => {
    if (grams < 1) return `${Math.round(grams * 1000)} mg`;
    return `${grams.toFixed(2)} g`;
};

const calculateMetrics = () => {
    if (typeof window === 'undefined' || !window.performance) return;

    const timing = window.performance.timing;
    const navigation = window.performance.getEntriesByType('navigation')[0] as PerformanceNavigationTiming;

    if (timing && timing.loadEventEnd > 0) {
        loadTime.value = timing.loadEventEnd - timing.navigationStart;
    }

    if (navigation && 'transferSize' in navigation) {
        const totalBytes = navigation.transferSize;
        if (totalBytes > 0) {
            const emissions = co2Calculator.perByte(totalBytes);
            co2Emission.value = emissions as number;
        }
    } else {
        const resourceEntries = window.performance.getEntriesByType('resource') as PerformanceResourceTiming[];
        const totalBytes = resourceEntries.reduce((total, entry) => {
            return total + (entry.transferSize || 0);
        }, 0);
        
        if (totalBytes > 0) {
            const emissions = co2Calculator.perByte(totalBytes);
            co2Emission.value = emissions as number;
        }
    }
};

onMounted(() => {
    if (window.performance) {
        calculateMetrics();
    } else {
        window.addEventListener('load', calculateMetrics);
    }
});
</script>

<style scoped></style>