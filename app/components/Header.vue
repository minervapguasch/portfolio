<template>
    <header class="w-full bg-transparent">
        <nav class="container mx-auto px-4 py-4">
            <div class="flex items-center justify-between">
                <ul class="flex gap-8 items-center justify-center mx-auto">
                    <li v-for="link in links" :key="link.label" class="animate-jello">
                        <NuxtLink :to="link.to" class="text-lg font-medium hover:text-[var(--color-primary)]">
                            <span :class="{ 'text-pop-up-top': route.path === link.to }">
                                {{ link.label }}
                            </span>
                        </NuxtLink>
                    </li>
                </ul>
            </div>

            <div class="flex items-center justify-end gap-2">
                <a href="https://github.com/minervapguasch" target="_blank" rel="noopener" class="btn btn-ghost btn-sm p-1 text-sm">
                    <Icon name="mdi:github" mode="svg" class="h-8 w-8" />
                </a>
                <a href="https://linkedin.com/in/polguaschromero" target="_blank" rel="noopener" class="btn btn-ghost btn-sm p-1 text-sm">
                    <Icon name="mdi:linkedin" mode="svg" class="h-8 w-8" />
                </a>
                <a href="https://instagram.com/__polguasch" target="_blank" rel="noopener" class="btn btn-ghost btn-sm p-1 text-sm">
                    <Icon name="mdi:instagram" mode="svg" class="h-8 w-8" />
                </a>
            </div>
        </nav>
    </header>
</template>

<script setup lang="ts">

const route = useRoute();
const links = [
    {
        label: 'Me',
        to: '/'
    },
    {
        label: 'My things',
        to: '/portfolio'
    },
    // {
    //     label: 'My thoughts',
    //     to: '/blog'
    // }
];

useHead({
    title: 'Pol Guasch Romero',
    meta: [
        { name: 'description', content: 'Pol Guasch Romero - Software Engineer' }
    ]
})
</script>

<style scoped>
.animate-jello:hover {
	animation: jello-horizontal 0.9s both;
}

@keyframes jello-horizontal {
	0% {
        transform: scale3d(1, 1, 1);
    }
    30% {
        transform: scale3d(1.05, 0.95, 1);
    }
    40% {
        transform: scale3d(0.95, 1.05, 1);
    }
    50% {
        transform: scale3d(1.05, 0.95, 1);
    }
    65% {
        transform: scale3d(0.95, 1.05, 1);
    }
    75% {
        transform: scale3d(1.05, 0.95, 1);
    }
    100% {
        transform: scale3d(1, 1, 1);
    }
}

.text-pop-up-top {
	animation: text-pop-up-top 0.5s cubic-bezier(0.250, 0.460, 0.450, 0.940) both;
}

@keyframes text-pop-up-top {
	0% {
		transform: translateY(0);
		transform-origin: 50% 50%;
        text-shadow: none;
	}
    100% {
        transform: translateY(-50px);
        transform-origin: 50% 50%;
        text-shadow: 0 1px 0 var(--tw-shadow-color), 0 2px 0 var(--tw-shadow-color), 0 3px 0 var(--tw-shadow-color), 0 4px 0 var(--tw-shadow-color), 0 5px 0 var(--tw-shadow-color), 0 6px 0 var(--tw-shadow-color), 0 7px 0 var(--tw-shadow-color), 0 8px 0 var(--tw-shadow-color), 0 9px 0 var(--tw-shadow-color), 0 10px 0 var(--tw-shadow-color);
    }
}
</style>