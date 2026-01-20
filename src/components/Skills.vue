<template>
    <section class="relative py-20 overflow-hidden" id="skills">
        <div class="relative z-10 max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="text-center mb-16" data-aos="fade-up">
                <h2 class="text-4xl md:text-5xl font-bold text-white mb-4">
                    <span class="text-transparent bg-clip-text bg-linear-to-r from-blue-400 to-cyan-400">
                        Skills
                    </span>& Experiences
                </h2>
                <p class="text-blue-200 text-lg max-w-2xl mx-auto">
                    My technical expertise and professional journey
                </p>
            </div>
            <div class="grid lg:grid-cols-2 gap-12 lg;gap-16">
                <div data-aos="fade-right">
                    <h3 class="text-2xl font-bold text-white mb-8 flex items-center gap-3">
                        Technical Skills
                    </h3>
                    <div class="space-y-6">
                        <div v-for="skill in skills" :key="skill.id" class="group">
                            <div class="flex items-center justify-between mb-3">
                                <span class="text-blue-200 font-semibold flex items-center gap-2">
                                    <component :is="skill.icon" class="w-5 h-5" :class="skill.iconColor"></component>
                                    {{ skill.title }}
                                </span>
                                <span :class="skill.percentageColor">
                                    {{ skill.percentage }} %
                                </span>
                            </div>
                            <div class="h-2 bg-gray-700 rounded-full overflow-hidden">
                                <div class="h-full rounded-full transition-all duration-1000 group-hover:scale-105"
                                    :class="skill.gradient" :style="{ width: skill.percentage + '%' }">

                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="mt-12">
                        <h4 class="text-xl font-bold text-white mb-6 flex items-center gap-2">
                            <Squares2X2Icon class="w-6 h-6 text-cyan-400" />
                            Tech Stack
                        </h4>
                        <div class="flex flex-wrap gap-3">
                            <span
                            v-for="tech in techStack"
                            :key="tech"
                            class="px-4 py-2 bg-linear-to-r from-blue-500/20 border border-blue-400/30 rounded-full text-blue-200 text-sm font-medium hover:scale-105 transition-transform duration-300">
                                {{ tech }}                                
                            </span>
                        </div>
                    </div>
                </div>
                <div data-aos="fade-left">
                    <h3 class="text-2xl font-bold text-white mb-8 flex items-center gap-3">
                        <BriefcaseIcon class="w-8 h-8 text-cyan-400"/>
                        Work Experiences
                    </h3>
                    <div class="space-y-8">
                        <div
                        v-for="exp in experiences"
                        :key="exp.id"
                        class="relative pl-8 border-l-2 group"
                        :class="exp.borderColor">
                            <div class="absolute -left-2 top-0 w-4 h-4 rounded-full group-hover:scale-150 transition-transform duration-300"
                            :class="exp.dotColor">
                            </div>
                            <div class="bg-linear-to-br from-gray-800/50 to-blue-900/30 rounded-2xl p-6 border backdrop-blur-sm group-hover:border-blue-400/40 transition-all duration-300"
                            :class="exp.borderClass">
                            <div class="flex flex-col sm:flex-row sm:items-center sm:justify-between mb-3">
                                <h4 class="text-lg font-bold text-white">
                                    {{ exp.position }}
                                </h4>
                                <span :class="exp.dateColor" class="mt-1 sm:mt-0"> {{ exp.period }}</span>
                            </div>
                            <p class="font-medium mb-3">
                                {{ exp.company }}
                            </p>
                            <p class="text-blue-100 text-sm leading-relaxed">
                                {{ exp.desc }}
                            </p>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>
<script setup>
import { CodeBracketIcon, ServerIcon, ShieldCheckIcon, CpuChipIcon, Squares2X2Icon, BriefcaseIcon } from '@heroicons/vue/16/solid';

const skills = [
    {
        id: 1,
        title: "Frontend Development",
        icon: CodeBracketIcon,
        iconColor: 'text-blue-400',
        percentage: 80,
        percentageColor: "text-blue-400 text-sm",
        gradient: 'bg-linear-to-r from-blue-500 to-cyan-500'
    },
    {
        id: 2,
        title: "Backend Development",
        icon: ServerIcon,
        iconColor: 'text-blue-400',
        percentage: 90,
        percentageColor: "text-blue-400 text-sm",
        gradient: 'bg-linear-to-r from-cyan-500 to-cyan-500'
    },
    {
        id: 3,
        title: "DevOps & Cloud",
        icon: ShieldCheckIcon,
        iconColor: 'text-blue-400',
        percentage: 65,
        percentageColor: "text-blue-400 text-sm",
        gradient: 'bg-linear-to-r from-blue-500 to-cyan-500'
    },
    {
        id: 4,
        title: "Discord Bot Development",
        icon: CpuChipIcon,
        iconColor: 'text-cyan-400',
        percentage: 75,
        percentageColor: "text-cyan-400 text-sm",
        gradient: 'bg-linear-to-r from-cyan-500 to-blue-500'
    },
]

const experiences = [
    {
        id: 1,
        position: "Laravel Developer",
        company: "Freelance / Self-Employed",
        period: "August 2025 - October 2025",
        desc: "Developed a web application called \"Schule Manager\" using Laravel for school management. This project involved creating features for managing students, teachers, and courses, while ensuring an intuitive and efficient user interface. ",
        borderColor: "border-blue-500/30",
        dotColor: "bg-blue-500",
        borderClass: "border-blue-500/20",
        dateColor: "text-blue-400 text-sm font-semibold",
        companyColor: "text-cyan-400"
    },
    {
        id: 2,
        position: "Symfony Developer",
        company: "Rna Dev Madagascar",
        period: "June 2023 - May 2024",
        desc: "Acquired skills in web development, database integration, and deployment.",
        borderColor: "border-blue-500/30",
        dotColor: "bg-blue-500",
        borderClass: "border-blue-500/20",
        dateColor: "text-blue-400 text-sm font-semibold",
        companyColor: "text-cyan-400"
    },
    {
        id: 3,
        position: "Intern Symfony Developer",
        company: "OMH Madagascar",
        period: "November 2022 - February 2023",
        desc: "Developed a web application for managing IT equipment, focusing on usability and user experience.",
        borderColor: "border-cyan-500/30",
        dotColor: "bg-cyan-500",
        borderClass: "border-cyan-500/20",
        dateColor: "text-cyan-400 text-sm font-semibold",
        companyColor: "text-blue-400"
    },
]

const techStack = [
    'Laravel', 'Symfony', 'Node Js', 'Python', 'Vue Js', 'Javascript', 'TypeScript', 'Tailwind CSS', 'Bootstrap', 'Ajax', 'SQL', 'REST API', 'Docker'
]
</script>