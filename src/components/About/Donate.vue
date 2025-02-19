<template>
    <Card title="Donate Me" :isText="false">
        <template v-slot:content>
            <p class="donation-text">
                If you like what I'm doing you can support me via Ko-Fi.
            </p>
            <br>
            <a href="https://ko-fi.com/adamkaisa" target="_blank" class="donate-button">
                <Heart class="donate-icon" />
                Ko-Fi
            </a>
        </template>
    </Card>
</template>

<style scoped>
/* Teks deskripsi donasi */
.donation-text {
  font-family: 'El Messiri', sans-serif ;
  margin: 0;
  width: auto;
  font-size: 1rem;
  line-height: 1.5;
  color: #3d3b3c;
  text-align: center;
}

.dark .donation-text {
  color: #d1d5db;
}

/* Tombol donasi */
.donate-button {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 8px;
  width: 100%;
  padding: 10px;
  font-size: 1.25rem;
  font-weight: bold;
  text-decoration: none;
  color: #3b82f6;
  border: 2px solid #3b82f6;
  border-radius: 8px;
  transition: all 0.3s ease;
}

.donate-button:hover {
  background-color: #3b82f6;
  color: white;
  transform: scale(1.05);
}

.donate-button:active {
  transform: scale(0.95);
}

/* Ikon dalam tombol */
.donate-icon {
  width: 24px;
  height: 24px;
  stroke: #3b82f6;
  transition: all 0.3s ease;
}

.donate-button:hover .donate-icon {
  stroke: #ff5a16;
  fill: #ff5a16;
}
</style>
