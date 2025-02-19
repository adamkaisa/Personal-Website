<template>
    <RouterView v-slot="{ Component, route }">
        <Transition
            :enter-active-class="route.meta.enter as string || ''"
            :leave-active-class="route.meta.leave as string || ''"
            :onAfterEnter="() => (show_ = true)"
        >
            <KeepAlive>
                <component :is="Component" :key="route.path" />
            </KeepAlive>
        </Transition>
    </RouterView>
</template>

<script setup lang="ts">
    import { useThemeStore } from './stores/theme'

    const themeStore = useThemeStore()
    const theme = computed(() => themeStore.theme)

    const show_ = ref(false)

    useHead({
        titleTemplate: (title?: string) => (title ? `${title} | Adam Khairusydan` : 'Adam Khairusydan'),
        link: [{ rel: 'icon', type: 'image/png', sizes: 'any', href: '/favicon.png' }]
    })

    // watch effect
    watchEffect(() => {
    document.documentElement.classList.toggle('dark', !theme.value)
    document.documentElement.classList.toggle('light', theme.value)
})

    onMounted(() => {
        show_.value = true
    })
</script>