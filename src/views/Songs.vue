<template>
    <div class="sc-page sc-flex-center relative">
        <BackButton name="Songs" class="absolute left-5 top-5" />

        <div class="content sc-flex-center w-9/10 mt-25 mb-5 flex-col gap-10">
            <Suspense>
                <SongList />
            </Suspense>
        </div>

        <!-- Scroll Down Icon -->
        <div
            v-if="showScrollDown"
            class="scroll-down fixed bottom-5 right-5 cursor-pointer"
            @click="scrollToBottom">
            <ArrowDown />
        </div>
    </div>
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue'
import ArrowDown from '@/assets/svg/ArrowDown.vue'

useHead({ title: 'Projects' })

const showScrollDown = ref(false)

const checkScroll = () => {
    const scrolledToBottom = window.innerHeight + window.scrollY >= document.body.scrollHeight - 10
    showScrollDown.value = !scrolledToBottom
}

const scrollToBottom = () => {
    window.scrollTo({
        top: document.body.scrollHeight,
        behavior: 'smooth'
    })
}

onMounted(() => {
    checkScroll()
    window.addEventListener('scroll', checkScroll)
    window.addEventListener('resize', checkScroll)
})

onUnmounted(() => {
    window.removeEventListener('scroll', checkScroll)
    window.removeEventListener('resize', checkScroll)
})
</script>

<style scoped>
.scroll-down {
    width: 50px;
    height: 50px;
    background: #1d1d1d;
    color: white;
    padding: 10px;
    border-radius: 50%;
    transition: opacity 0.3s, transform 0.3s;
    display: flex;
    align-items: center;
    justify-content: center;
}

.scroll-down:hover {
    opacity: 0.8;
    transform: scale(1.1);
}

.scroll-down svg {
    width: 30px;
    height: 30px;
    stroke: #444;
}
</style>

