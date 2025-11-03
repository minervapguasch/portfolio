<template>
    <ClientOnly>
        <CardContainer>
            <CardBody
                class="group/card relative size-auto rounded-xl border border-base-300 bg-neutral p-6 sm:w-[30rem] hover:shadow-2xl hover:shadow-primary/[0.1]">
                <CardItem :translate-z="50" class="text-xl font-bold text-base-content">
                    {{ props.title }}
                </CardItem>
                <CardItem as="p" translate-z="60" class="mt-2 max-w-sm text-sm text-base-content/70 text-justify">
                    {{ props.description }}
                </CardItem>

                <!-- Tech badges -->
                <CardItem :translate-z="70" class="mt-4 w-full">
                    <div class="flex flex-wrap gap-2">
                        <span v-for="techItem in props.tech" :key="techItem" class="badge badge-outline text-xs">{{ techItem }}</span>
                    </div>
                </CardItem>
                <CardItem :translate-z="100" :rotate-x="20" :rotate-z="-10" class="mt-4 w-full">
                    <img :src="props.image"
                        height="1000" width="1000"
                        class="h-60 w-full rounded-xl object-cover group-hover/card:shadow-xl" alt="thumbnail" />
                </CardItem>
                <div class="mt-20 flex items-center justify-between">
                    <CardItem :translate-z="20" :translate-x="-40" as="a" href="https://rahulv.dev" target="__blank"
                        class="rounded-xl px-4 py-2 text-xs font-normal text-base-content" v-if="props.linkText">
                        {{ props.linkText }}
                    </CardItem>
                    <CardItem :translate-z="20" :translate-x="40" as="button"
                        class="rounded-xl bg-primary px-4 py-2 text-xs font-bold text-primary-content" v-if="props.buttonText" @click="goToActionButtonLink()">
                        {{ props.buttonText }}
                    </CardItem>
                </div>
            </CardBody>
        </CardContainer>
    </ClientOnly>
</template>

<script setup lang="ts">
const props = defineProps<{
    title: string,
    description: string,
    tech: string[],
    image: string,
    linkText?: string,
    link?: string,
    buttonText?: string,
    actionButtonLink?: string,
}>();

const goToActionButtonLink = () => {
    if (props.actionButtonLink) {
        navigateTo(props.actionButtonLink, { external: true });
    }
}
</script>