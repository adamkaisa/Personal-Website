<template>
    <Card title="My Goals" :isText="false">
        <template v-slot:content>
            <div class="goals-container">
                <div class="goal-item">
                    <span class="goal-status done">Done</span>
                    <span class="goal-text">Graduated with a bachelor's degree in Informatics Engineering</span>
                </div>

                <ArrowDown class="goal-arrow" />

                <div class="goal-item">
                    <span class="goal-status current">Current</span>
                    <span class="goal-text">Find a job as a Full-Stack Developer/Data Analyst</span>
                </div>

                <ArrowDown class="goal-arrow" />

                <div class="goal-item">
                    <span class="goal-status next">Next</span>
                    <span class="goal-text">Get a proper job in the USA or Japan</span>
                </div>
            </div>
        </template>
    </Card>
</template>

<style scoped>
/* Container utama */
.goals-container {
  margin-top: 10px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 12px;
}

/* Item dalam goals */
.goal-item {
  font-family: 'El Messiri', sans-serif ;
  display: flex;
  align-items: center;
  justify-content: start;
  gap: 8px;
  width: 100%;
  border-radius: 8px;
  background-color: #A6A4A4;
  padding: 8px 12px;
  box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.1);
}

.dark .goal-item {
  background-color: #27272a; 
  box-shadow: none;
}

/* Status (label kecil) */
.goal-status {
  border-radius: 9999px;
  padding: 4px 8px;
  font-size: 0.75rem;
  font-weight: bold;
  text-transform: uppercase;
}

/* Status: Done */
.goal-status.done {
  background-color: #bbf7d0;
  color: #16a34a;
}

.dark .goal-status.done {
  background-color: #15803d;
  color: #22c55e;
}

/* Status: Current */
.goal-status.current {
  background-color: #fef08a;
  color: #ca8a04;
}

.dark .goal-status.current {
  background-color: #a16207;
  color: #fde047;
}

/* Status: Next */
.goal-status.next {
  background-color: #bfdbfe;
  color: #2563eb;
}

.dark .goal-status.next {
  background-color: #1e40af;
  color: #60a5fa;
}

/* Teks goal */
.goal-text {
  font-size: 1rem;
  color: #3d3b3c;
}

.dark .goal-text {
  color: #d1d5db;
}

/* Panah di tengah */
.goal-arrow {
  stroke: #282828;
}

.dark .goal-arrow {
  stroke: #52525b;
}
</style>
