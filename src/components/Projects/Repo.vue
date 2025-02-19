<template>
    <div class="custom-repo-container">
        <div class="custom-content">
            <div class="custom-header">
                <span class="custom-name">{{ name }}</span>

                <div class="custom-stats">
                    <span class="custom-stars">
                        <Star class="custom-icon-small" />
                        {{ stars }}
                    </span>
                    <span class="custom-forks">
                        <Branch class="custom-icon-small" />
                        {{ forks }}
                    </span>
                </div>
            </div>

            <span class="custom-description">{{ computedDescription }}</span>
            <a :href="url" class="custom-link">
                <ArrowUpRight class="custom-icon-large" />
            </a>
        </div>
    </div>
</template>

<script setup lang="ts">
    const props = defineProps({
        name: {
            type: String,
            required: true
        },
        description: {
            // string or null
            type: String,
            default: null
        },
        url: {
            type: String,
            required: true
        },
        stars: {
            type: Number,
            required: true
        },
        forks: {
            type: Number,
            required: true
        }
    })

    const computedDescription = computed(() => {
        if (!props.description) return 'No description provided.'
        return props.description.length > 120 ? props.description.slice(0, 120) + '...' : props.description
    })
</script>

<style scoped>

.custom-repo-container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 20px;
  padding: 20px;
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
  align-items: stretch;
}

@media (min-width: 768px) {
  .custom-repo-container {
    gap: 40px;
  }
}

/* Kontainer utama untuk content */
.custom-content {
  border-radius: 10px;
  font-family: 'El Messiri', sans-serif ;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  justify-content: flex-start;
  gap: 16px;
  background-color: #c9c8c7;
  padding: 24px;
  min-height: 280px;
  width: 100%;
  height: 100%;
  position: relative;
  transition: transform 0.2s ease-in-out, box-shadow 0.2s ease-in-out;
}

/* Hover efek untuk kartu */
.custom-content:hover {
  transform: translateY(-5px);
  box-shadow: 0px 6px 16px rgba(0, 0, 0, 0.12);
}


.dark .custom-content {
  background-color: #222222;
}

/* Header */
.custom-header {
  font-family: 'Varoste', sans-serif ;
  letter-spacing: 2px;
  display: flex;
  align-items: center;
  width: 100%;
  gap: 8px;
}

.custom-name {
  flex-grow: 1;
  font-size: 1.4rem;
  font-weight: bold;
  color: #3d3b3c;
}

.dark .custom-name {
  color: #e5e7eb;
}

/* Stats */
.custom-stats {
  display: flex;
  flex-basis: 40%;
  align-items: center;
  justify-content: space-evenly;
  border-radius: 8px;
  background-color: #807E7E;
  padding: 8px 12px;
  font-size: 1.25rem;
  color: #3d3b3c;
  font-weight: 600;
}

.dark .custom-stats {
  background-color: #404040;
  color: #d1d5db;
}

.custom-stars,
.custom-forks {
  display: flex;
  align-items: center; 
  gap: 6px; 
}

/* Icon kecil */
.custom-icon-small {
  height: 1.5rem;
  width: 1.5rem;
  stroke: #3d3b3c;
}

.dark .custom-icon-small {
  stroke: #d1d5db;
}

/* Deskripsi */
.custom-description {
  word-break: break-word;
  font-size: 1.1rem;
  font-weight: 400;
  color: #404040;
  line-height: 1.5;
}

.dark .custom-description {
  color: #d1d5db;
}

@media (min-width: 768px) {
  .custom-description {
    width: 85%;
  }
}

.custom-link {
  position: absolute;
  bottom: 12px;
  right: 12px;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 50%;
  background-color: #c9c8c7;
  padding: 12px;
  transition: all 0.3s ease-in-out;
  outline: 5px solid #f2f0ef;
}

.custom-link:hover {
  outline-color: transparent;
  box-shadow: 0px 0px 15px #171717;
  background: #949392;
}

.dark .custom-link {
  background-color: #404040;
  outline-color: #171717;
}

.dark .custom-link:hover {
  box-shadow: 0px 0px 15px #949392;
  background: #b3b3b3;
}

.custom-icon-large {
  height: 2.4rem;
  width: 2.4rem;
  stroke: #3d3b3c;
}

.dark .custom-icon-large {
  height: 2.4rem;
  width: 2.4rem;
  stroke: #d1d5db;
}

.dark .custom-icon-large:hover {
  stroke: #121212;
}

/* Container utama */
.custom-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  border-radius: 8px;
  background-color: #c9c8c7;
  padding: 20px;
  box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.1);
  font-family: 'El Messiri', sans-serif ;
}

.dark .custom-container {
  background-color: #282828;
  box-shadow: none;
}

/* Judul */
.custom-container h1 {
  font-size: 1.5rem;
  font-weight: bold;
  color: #1e293b;
  margin: 0;
  text-align: center;
}

.dark .custom-container h1 {
  color: #e5e7eb;
}

/* Paragraf / Slot */
.custom-container p {
  font-size: 1rem;
  color: #475569;
  line-height: 1.5;
  text-align: center;
}

.dark .custom-container p {
  color: #d1d5db;
}

/* Slot konten */
.custom-slot {
  width: 100%;
}

@media (max-width: 768px) {
  .custom-repo-container {
    display: flex;
    flex-direction: column; 
    padding: 10px;
    gap: 12px;
    width: 100%;
    box-sizing: border-box;
  }

  .custom-content {
    display: flex;
    flex-direction: column;
    width: 100%;
    max-width: 100%;
    padding: 16px;
    min-height: auto;
    gap: 10px;
    box-sizing: border-box;
  }

  .custom-header {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
    width: 100%;
  }

  .custom-stats {
    font-size: 1rem;
    padding: 6px 10px;
    width: auto;
    flex-grow: 1;
    display: flex;
    justify-content: space-between;
  }

  .custom-description {
    font-size: 1rem;
    text-align: left;
    width: 100%;
    word-wrap: break-word;
  }

  .custom-link {
    position: relative;
    margin-left: auto;
    width: 36px;
    height: 36px;
    padding: 6px;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
}
  .custom-icon-large {
    height: 1.8rem;
    width: 1.8rem;
  }
}


</style>