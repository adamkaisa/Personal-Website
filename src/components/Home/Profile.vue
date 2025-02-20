@import url('https://fonts.googleapis.com/css2?family=Outfit:wght@100..900&display=swap');
@import url('https://fonts.googleapis.com/css2?family=El+Messiri:wght@400..700&display=swap');

@font-face {
  font-family: 'Varoste';
  src: url('/fonts/Varoste.otf') format('opentype'),
       url('/fonts/Varoste.ttf') format('truetype');
  font-style: normal;
  font-display: swap;
}


html,
body,
#app {
    
    min-height: 100vh;
    margin: 0;
    padding: 0;
    // overflow: scroll;
    overflow-x: hidden;
    -ms-overflow-style: none;
    scrollbar-width: none;
}

::-webkit-scrollbar {
    width: 8px;
    height: 8px;  
  }
  
  /* Track */
  ::-webkit-scrollbar-track {
    border-radius: 10px;
  }
   
  /* Handle */
  ::-webkit-scrollbar-thumb {
    background: linear-gradient(68.3deg, rgb(23, 41, 77) 6.3%, rgb(243, 113, 154) 90.9%);
    border-radius: 10px;
  }
  
  /* Handle on hover */
  ::-webkit-scrollbar-thumb:hover {
    background: linear-gradient(68.3deg, rgb(23, 41, 77) 6.3%, rgb(243, 113, 154) 90.9%);  }

.light body {
    background: #f0f0f0;
    background-attachment:fixed;
}

.dark body {
  background: #171717;
    background-attachment:fixed;
}

* {
    box-sizing: border-box;
}



.profile-container {
  position: relative;
  width: 100vw;
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
}

.marquee-container {
  position: absolute;
  top: 50%;
  left: 50%;
  width: 100vw;
  overflow: hidden;
  white-space: nowrap;
  transform: translate(-50%, -50%);
}

.marquee {
  display: flex;
  width: max-content;
  animation: marquee 100s linear infinite;
  color: #3d3b3c;
}

.dark .marquee span {
  color: #f2f0ef;
}

.marquee span {
  font-family: 'Varoste', sans-serif ;
  font-weight: 500;
  font-size: 20rem;
  padding-right: 2rem;
}

@keyframes marquee {
  from {
      transform: translateX(0%);
  }
  to {
      transform: translateX(-50%);
  }
}
.marquee {
  animation: marquee 200s linear infinite;
}

.profile-avatar {
  position: absolute;
  top: 20px;
  right: 20px;
  width: 50px;
  height: 50px;
  border-radius: 20%;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.3);
  transition: transform 0.3s ease-in-out;
}


.presence {
  position: absolute;
  top: 20px; 
  right: 80px;
  display: flex;
  align-items: center;
  gap: 10px;

  padding: 8px 12px;
  border-radius: 8px;
}

.status {
  display: flex;
  align-items: center;
  gap: 5px;
  font-size: 16px;
  color: white;
}

.status-icon {
  width: 12px;
  height: 12px;
  border-radius: 50%;
}

.divider {
  width: 4px;
  height: 4px;
  background: #3d3b3c;
  border-radius: 50%;
}

.dark .divider {
  background: #f2f0ef;
}

.custom-status {
  font-size: 14px;
  color: #bbb;
}

.links {
  position: absolute;
  top: 20px;
  right: -1%;
  display: flex;
  flex-direction: row; 
  gap: 10px;
}

.links a {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 40px;
  height: 40px;
  background: #c9c8c7;
  border-radius: 8px;
  transition: background 0.3s ease;
}

.links a:hover {
  background: #949392;
}

.dark .links a:hover {
  background: #3d3b3c;
}

.dark .links a {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 40px;
  height: 40px;
  background: #282828;
  border-radius: 8px;
  transition: background 0.3s ease;
}

.links a > * {
  stroke: #3d3b3c;
  transition: stroke 0.3s ease;
}

.dark .links a > * {
  stroke: #f2f0ef;
}

@media (max-width: 768px) {
  .links {
    flex-direction: column;
    align-items: flex-start;
    left: 20px;
    right: auto;
  }
}
