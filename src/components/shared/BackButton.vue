<template>
    <span class="sc-flex-center w-max gap-5">
        <RouterLink to="/" class="back-button sc-flex-center rd-full group p-2 transition-all duration-300">
            <ArrowLeft class="back-icon h-8 w-8" />
        </RouterLink>
        <span class="page-name">{{ name }}</span>
    </span>
</template>

<script setup lang="ts">
    defineProps({
        name: {
            type: String,
            required: true
        }
    })
</script>

<style scoped>

.page-name {
  font-family: 'Varoste', sans-serif ;
  display: none;
  font-size: 1.875rem;
}

@media (min-width: 768px) {
  .page-name {
    display: block;
  }
}

/* Warna latar tombol */
.back-button {
    background-color: #c9c8c7;
}

.back-button:hover {
    background-color: #949392;
}

.dark .back-button {
    background-color: #262626;
}

.dark .back-button:hover {
    background-color: #404040;
}

/* Warna ikon */
.back-icon {
    stroke: #3d3b3c;
    transition: stroke 0.3s ease-in-out;
}

.dark .back-icon {
    stroke: #c9c8c7;
}

/* Warna teks */
.page-name {
    color: #3d3b3c;
}

.dark .page-name {
    color: #c9c8c7;
}
</style>
