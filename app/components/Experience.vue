<template>
    <section id="experience" class="min-h-screen bg-base-100 py-24">
        <div class="max-w-4xl mx-auto px-6">
            <header class="mb-14 space-y-3">
                <p class="text-xs font-medium uppercase tracking-[0.35em] text-base-content/60">Journey</p>
                <h2 class="text-3xl font-semibold text-base-content">Experience</h2>
                <p class="text-sm text-base-content/70 max-w-xl">
                    A distilled view of the roles that shaped my approach to product and software engineering, and made me reconsider the choices I make every day.
                </p>
            </header>

            <ol class="relative border-l border-base-300/40 ml-3 space-y-12">
                <li
                    v-for="item in experiences"
                    :key="item.company"
                    class="pl-8"
                >
                    <span class="absolute -left-[7px] mt-1 flex h-3 w-3 items-center justify-center rounded-full border border-base-300 bg-base-100"></span>
                    <div class="space-y-3">
                        <div class="flex flex-col gap-2 sm:flex-row sm:items-center sm:justify-between">
                            <div>
                                <h3 class="text-lg font-medium text-base-content">{{ item.role }}</h3>
                                <p class="text-sm text-base-content/60">{{ item.company }}</p>
                            </div>
                            <span class="text-xs uppercase tracking-[0.2em] text-base-content/50">{{ item.period }}</span>
                        </div>
                        <p class="text-sm text-base-content/70 leading-relaxed">{{ item.summary }}</p>
                        <ul class="space-y-1 text-sm text-base-content/60">
                            <li v-for="point in item.points" :key="point" class="flex gap-2">
                                <span class="text-base-content/40">•</span>
                                <span>{{ point }}</span>
                            </li>
                        </ul>
                        <div class="flex flex-wrap gap-2 pt-1">
                            <span v-for="tech in item.tech" :key="tech" class="badge badge-outline badge-xs">{{ tech }}</span>
                        </div>
                    </div>
                </li>
            </ol>
        </div>
    </section>
</template>

<script setup lang="ts">
const experiences = [
    {
        role: 'Co-Founder & Chief Technology Officer',
        company: 'Trendia',
        period: '2022 – Present',
        location: 'Remote',
        summary: 'Co-founding a startup that helps brands and content creators keep track of the trends on social media, allowing them to stay ahead of the competition and create better content that resonates with their audience.',
        points: [
            'Development of the SaaS platform to help brands and content creators keep track of the trends on social media.',
            'Development of the different propertary AI models to analyse and categorize content on social media.',
            'Integration of the different AI models in a continous data pipeline.',
        ],
        tech: ['Nuxt 4', 'Bun', 'PostgreSQL', 'Docker', 'RabbitMQ', 'AWS', 'Linux']
    },
    {
        role: 'Senior Data Engineer & Software Engineer',
        company: 'Minerva Data Solutions',
        period: '2023 – Present',
        location: 'Andorra',
        summary: 'Developing and integrating software solutions for companies and clients.',
        points: [
            'Development of a Machine Learning model to predict and classify demand of public transport for the Government of Andorra.',
            'Developmenf of a data pipeline for real-time image processing and analysis for a famous cooking spanish TV show.',
            'Architecting the data layer of a company that provides tourism services.',
        ],
        tech: ['Python', 'Nuxt 4', 'Bun', 'PostgreSQL', 'Docker']
    },
    {
        role: 'Data Engineer',
        company: 'Wizata',
        period: '2022 – 2023',
        location: 'Remote',
        summary: 'Developed Machine Learning solutions and data pipelines for various clients in the Industry 4.0 domain.',
        points: [
            'Developed a Machine Learning model to predict and classify rotatory machine failures with 2D vibration sensors data.',
            'Maintained data simulation pipelines for development and testing of the platform.',
            'Generation of synthetic data and development of streaming pipeline in Azure EventHub for real-time data simulation.',
        ],
        tech: ['Python', 'TensorFlow', 'Kafka', 'Azure', 'Docker']
    },
    {
        role: 'Data Engineer',
        company: 'Tag Systems',
        period: '2020 - 2022',
        location: 'Andorra',
        summary: 'Developed and maintained data pipelines for internal data related to maintenance and operations of the company.',
        points: [
            'Data warehouse of maintenance activities in MongoDB',
            'Built a modular preventive maintenance system in Node.js and MongoDB',
        ],
        tech: ['Node.js', 'MongoDB', 'Python']
    }
]
</script>
