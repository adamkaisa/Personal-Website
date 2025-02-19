<template>
    <div class="copyright">
      © 2025 Adam Khairusydan. All rights reserved.
    </div>
</template>
  
<style>
    .copyright {
        position: fixed;
        bottom: 1.5rem;
        right: 1rem;
        font-size: 0.875rem;
        color: #3d3b3c;
        font-family: 'Varoste', sans-serif ;
        letter-spacing: 1px;
    }

    .dark .copyright {  
        color: #f2f0ef;
    }

    @media (max-width: 768px) {
    .copyright {
        right: 50%;
        transform: translateX(50%);
        text-align: center;
        width: 100%;
        bottom: 1rem; 
    }
}

</style>
