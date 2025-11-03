<template>
    <div class="grid grid-cols-1 md:grid-cols-2 max-w-7xl mx-auto">
        <div v-for="project in projects" :key="project.title">
            <ProjectCard
                :title="project.title"
                :description="project.description"
                :tech="project.tech"
                :image="project.imageSrc"
                :link-text="project.linkText"
                :link="project.link"
                :button-text="project.buttonText"
                :action-button-link="project.actionButtonLink"
            />
        </div>
    </div>
</template>

<script setup lang="ts">
interface Project {
    title: string,
    tech: string[],
    description: string,
    imageSrc: string,
    linkText?: string,
    link?: string,
    buttonText?: string,
    actionButtonLink?: string,
}

const projects: Project[] = [
    {
        title: 'CATBench', 
        description: 'CATBench is a benchmark to know which propietary LLMs are better handlening, generating and working with the Catalan language. The goal of this benchmark is to help developers choose and see which are the tradeoffs between different models when working in Catalan, analysing their performance with the language also taking into account costs and performance.',
        tech: ['Elixir', 'Nuxt 4'],
        imageSrc: '/catbench.png',
        linkText: 'Check out the repo',
        link: 'https://www.google.com',
        buttonText: 'Fes-hi una ullada',
        actionButtonLink: 'https://catbench.guasch.dev',
    },
    {
        title: 'Trendia',
        tech: ['Nuxt 4', 'Tailwind CSS'],
        description: 'Trendia is a platform that helps brands and content creators keep track of the trends on social media, allowing them to stay ahead of the competition and create better content that resonates with their audience.',
        imageSrc: '/trendia.png',
        linkText: 'Check out the website',
        link: 'https://www.trendia.ai',
        buttonText: 'Track the trends',
        actionButtonLink: 'https://www.trendia.ai',
    },
    {
        title: 'KiThumbs',
        tech: ['Vue 3', 'Tailwind CSS', 'Pinia', 'Vue Router'],
        description: 'KiThumbs helps YouTube creators generate thumbnails for their videos in seconds instead of hours. Professional-grade results with any trained avatar, giving the video makers the freedom to create any thumbnail they need.',
        imageSrc: '/kithumbs.png',
        linkText: 'Check out the website',
        link: 'https://www.kithumbs.com',
        buttonText: 'Generate thumbnails',
        actionButtonLink: 'https://www.kithumbs.com',
    },
];
</script>

<style scoped>

</style>