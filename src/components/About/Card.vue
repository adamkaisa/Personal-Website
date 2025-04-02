<template>
  <div class="custom-container font-nunito">
      <img :src="avatar" alt="User Avatar" class="profile-avatar" />
      <h1 class="custom-title">{{ title }}</h1>
      <p class="custom-text" v-if="isText">
          <slot></slot>
      </p>
      <div class="custom-slot">
          <slot name="content"></slot>
      </div>
  </div>
</template>

<script setup lang="ts">
defineProps({
  title: {
      type: String,
      required: true
  },
  isText: {
      type: Boolean,
      default: true
  }
});

const avatar = new URL('@/assets/profile.jpg', import.meta.url).href;
</script>


<style scoped>

/* Container utama */
.custom-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  border-radius: 8px;
  background-color: #c9c8c7;
  padding: 20px;
  margin-top: 3%;
  margin-bottom: -3%;
  box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.1);
}

.dark .custom-container {
  background-color: #222222;
  box-shadow: none;
}

/* Judul */
.custom-title {
  font-family: 'KATSUMI', sans-serif ;
  letter-spacing: 2px;
  font-size: 1.5rem;
  font-weight: bold;
  color: #3d3b3c;
  margin: 0;
  text-align: center;
}

.dark .custom-title {
  color: #e5e7eb;
}

/* Paragraf / Slot */
.custom-text {
  font-size: 1rem;
  line-height: 1.5;
  text-align: left;
  padding-left: 200px;

}
.dark .custom-text {
  color: #d1d5db;
}

/* Slot konten */
.custom-slot {
  width: 100%;
}

@media (max-width: 768px) {
    .custom-container {
        margin-top: 40%;
        margin-bottom: -40%;
        padding: 10px;
    }

    .custom-title {
        font-size: 1.1rem;
        text-align: center;
    }

    .custom-text {
        font-size: 0.85rem;
        text-align: center;
        padding-left: 0;
        padding-right: 0;
    }

    .custom-slot {
        width: 100%;
        padding: 5px;
    }
}

.profile-avatar {
    left: 12%;
    right: 0;
    top: auto;
    bottom: 53%;
    width: 250px;
    height: 250px;
    border-radius: 20%;
    border: 2px solid #c9c8c7;
    box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.1);
}
    
.dark .profile-avatar {
    border: 2px solid #171717;
}
    
@media (max-width: 768px) {
    .profile-avatar {
        position: absolute;
        top: 60px;
        left: 50%;
        transform: translateX(-50%);
        width: 150px;
        height: 150px;
    }
}
</style>
