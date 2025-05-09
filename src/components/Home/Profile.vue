<template>
    <div class="profile sc-flex-center font-nunito flex-row flex-wrap-reverse gap-5 md:gap-10" v-if="user">
        <div class="profile-info flex-items-start flex-content-center flex w-auto flex-col gap-4">
            <span class="name font-roboto text-5xl font-bold tracking-wide">
                <div class="marquee-container">
                    <div class="marquee">
                        <div class="marquee-content">
                            <span v-for="i in 10" :key="i">ADAM KHAIRUSYDAN✽</span>
                        </div>
                        <div class="marquee-content">
                            <span v-for="i in 10" :key="i">ADAM KHAIRUSYDAN✽</span>
                        </div>
                    </div>
                </div>
            </span>
            <div class="presence sc-flex-center gap-3 text-lg">
                <span class="status sc-flex-center">
                    <span
                        class="status-icon mr-1 inline-block h-4 w-4 rounded-full"
                        :style="{ backgroundColor: statusColor }"
                    ></span>
                    <span class="status-text text-slate-700 dark:text-neutral-400">{{ user.status }}</span>
                </span>

                <span class="divider inline-block h-1 w-1 rounded-full bg-slate-300 dark:bg-neutral-900"></span>
                <span class="custom-status text-slate-500 dark:text-neutral-400">{{
                    user.custom_status || randomQuote
                }}</span>
            </div>

            <span class="links flex w-full items-center justify-start gap-4">
                <a
                    v-for="link in links"
                    :href="link.href"
                    target="_blank"
                    class="sc-flex-center rd-2 group p-2 transition-all duration-300"
                >
                    <component :is="link.icon" class="h-7 w-7" />
                </a>
            </span>


        </div>

        <img :src="user.avatar" alt="" class="profile-avatar rd-2 shadow-avatar-color h-64 w-64 shadow-lg" />
    </div>
</template>

<script setup lang="ts">
    import { useDiscordStore } from '@/stores/discord'
    // @ts-ignore
    import ColorThief from '@/assets/js/color-thief.mjs'
    const colorThief = new ColorThief()

    const discordStore = useDiscordStore()
    const user = computed(() => discordStore.user)

    const colors = {
        online: '#43b581',
        idle: '#faa61a',
        dnd: '#f04747',
        offline: '#747f8d'
    }

    const statusColor = computed((): string => {
        const status = user.value?.status
        if (!status) return colors.offline
        // @ts-ignore
        return colors[status]
    })

    const randomQuote = computed(() => {
        const quotes = [
            '👨‍💻😅',
            '👨‍💻😓',
            '👨‍💻😫',
            '👨‍💻😭',
            '👨‍💻🤕'
        ]
        return quotes[Math.floor(Math.random() * quotes.length)]
    })

    const links = [
        {
            href: 'mailto:khairusydan99@gmail.com',
            icon: defineAsyncComponent(() => import('@/assets/svg/AtSign.vue'))
        },
        {
            href: 'https://www.linkedin.com/in/adamkhairusydan/',
            icon: defineAsyncComponent(() => import('@/assets/svg/LinkedIn.vue'))
        },
        {
            href: 'https://github.com/adamkaisa',
            icon: defineAsyncComponent(() => import('@/assets/svg/GitHub.vue'))
        },
        {
            href: 'https://discord.com/users/474239882877730837',
            icon: defineAsyncComponent(() => import('@/assets/svg/Discord.vue'))
        }
    ]

    const emit = defineEmits(['fetch-failed'])

    const fetchUser = async () => {
        try {
            await discordStore.fetchUser()
        } catch (error) {
            emit('fetch-failed', error)
        }
    }

    await fetchUser()

    onMounted(() => {
        setInterval(fetchUser, 1000 * 30)

        const img: HTMLImageElement | null = document.querySelector('.profile-avatar')
        if (!img) return
        img.crossOrigin = 'Anonymous'
        if (img.complete) {
            const color = colorThief.getColor(img)
            document.documentElement.style.setProperty('--avatar-color', `rgb(${color.join(',')}, 0.7)`)
        } else {
            img.addEventListener('load', () => {
                const color = colorThief.getColor(img)
                document.documentElement.style.setProperty('--avatar-color', `rgb(${color.join(',')}, 0.7)`)
            })
        }
    })
</script>
