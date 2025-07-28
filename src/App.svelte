<script>
  import { onMount } from 'svelte';
  import { fade } from 'svelte/transition';
  
  // Состояние анимаций
  let animationsStarted = false;
  let isShowingLogo = true;
  let visibleAnimations = {
    anim1: false,
    anim2: false,
    anim3: false,
    anim4: false
  };
  
  // Конфигурация времени появления
  const animationDelays = {
    anim1: 0,
    anim2: 0,
    anim3: 2000,
    anim4: 3500
  };
  
  // Скриншоты для переключения
  const screenshots = [
    '/all-bgc/STOP/STOP Motion00011130.png',
    '/all-bgc/STOP/STOP Motion00011131.png',
    '/all-bgc/STOP/STOP Motion00011132.png',
    '/all-bgc/STOP/STOP Motion00011133.png',
    '/all-bgc/STOP/STOP Motion00011134.png',
    '/all-bgc/STOP/STOP Motion00011135.png',
    '/all-bgc/STOP/STOP Motion00011136.png',
    '/all-bgc/STOP/STOP Motion00011137.png',
    '/all-bgc/STOP/STOP Motion00011138.png',
    '/all-bgc/STOP/STOP Motion00011139.png',
    '/all-bgc/STOP/STOP Motion00011140.png',
    '/all-bgc/STOP/STOP Motion00011141.png',
    '/all-bgc/STOP/STOP Motion00011142.png',
    '/all-bgc/STOP/STOP Motion00011143.png',
    '/all-bgc/STOP/STOP Motion00011144.png',
    '/all-bgc/STOP/STOP Motion00011145.png',
    '/all-bgc/STOP/STOP Motion00011146.png',
    '/all-bgc/STOP/STOP Motion00011147.png',
    '/all-bgc/STOP/STOP Motion00011148.png',
    '/all-bgc/STOP/STOP Motion00011149.png',
    '/all-bgc/STOP/STOP Motion00011150.png',
    '/all-bgc/STOP/STOP Motion00011151.png',
    '/all-bgc/STOP/STOP Motion00011152.png',
    '/all-bgc/STOP/STOP Motion00011153.png',
    '/all-bgc/STOP/STOP Motion00011154.png',
    '/all-bgc/STOP/STOP Motion00011155.png',
    '/all-bgc/STOP/STOP Motion00011156.png'
  ];
  
  let currentLogo = '/all-bgc/logo.webp';
  
  // Функция запуска анимаций
  function startAnimations() {
    if (animationsStarted) return;
    
    animationsStarted = true;
    console.log('Анимации запущены!');
    
    // Показываем анимации по расписанию
    setTimeout(() => {
      visibleAnimations.anim1 = true;
      visibleAnimations = visibleAnimations;
    }, animationDelays.anim1);
    
    setTimeout(() => {
      visibleAnimations.anim2 = true;
      visibleAnimations = visibleAnimations;
    }, animationDelays.anim2);
    
    setTimeout(() => {
      visibleAnimations.anim3 = true;
      visibleAnimations = visibleAnimations;
    }, animationDelays.anim3);
    
    setTimeout(() => {
      visibleAnimations.anim4 = true;
      visibleAnimations = visibleAnimations;
    }, animationDelays.anim4);
  }
  
  // Функция переключения логотипа
  function toggleLogo() {
    console.log('Клик по логотипу!');
    if (!animationsStarted) {
      startAnimations();
    }
    
    if (isShowingLogo) {
      // Показываем случайный скриншот
      const randomScreenshot = screenshots[Math.floor(Math.random() * screenshots.length)];
      currentLogo = randomScreenshot;
      isShowingLogo = false;
      console.log('Переключился на скриншот:', randomScreenshot);
    } else {
      // Возвращаемся к логотипу
      currentLogo = '/all-bgc/logo.webp';
      isShowingLogo = true;
      console.log('Переключился на логотип');
    }
  }
  
  onMount(() => {
    console.log('Компонент загружен!');
    console.log('Текущий логотип:', currentLogo);
  });
</script>

<svelte:head>
  <style>
    :global(body) {
      background: #181818;
      margin: 0;
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: flex-start;
      position: relative;
      overflow-x: hidden;
      padding-top: 80px;
    }
    
    /* Видео фон */
    .background-video {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      object-fit: cover;
      z-index: -1;
      opacity: 1.0;
    }
    
    /* Логотип */
    .top-video {
      max-width: 40%;
      position: relative;
      z-index: 9999;
      cursor: pointer;
      margin-top: 2%;
    }
    
    /* Анимации */
    .anim {
      opacity: 0;
      transition: opacity 1s ease;
      background: none;
      display: block;
      position: relative;
      z-index: 1;
    }
    
    .anim.visible {
      opacity: 1;
    }
    
    /* Фиксированные проценты для всех анимаций */
    #anim1 {
      max-width: 30% !important;
      margin-top: -8% !important;
    }
    
    #anim2 {
      max-width: 35% !important;
      margin-top: -14% !important;
    }
    
    #anim3 {
      max-width: 20% !important;
      margin-top: -8% !important;
    }
    
    #anim4 {
      max-width: 20% !important;
      margin-top: -8% !important;
    }
    
    /* Контейнер для всех элементов */
    .main-container {
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: flex-start;
      width: 100%;
      height: calc(100vh - 80px);
      margin-top: 0;
    }
    
    /* Мобильная версия - упрощенная */
    @media (max-width: 768px) {
      body {
        padding-top: 60px !important;
      }
      
      .main-container {
        width: 100% !important;
        max-width: 100% !important;
        margin-top: 0 !important;
        height: calc(100vh - 60px) !important;
      }
      
      .top-video {
        max-width: 60% !important;
        margin-top: 5% !important;
      }
      
      #anim1 {
        max-width: 50% !important;
        margin-top: 2% !important;
      }
      
      #anim2 {
        max-width: 55% !important;
        margin-top: 2% !important;
      }
      
      #anim3 {
        max-width: 40% !important;
        margin-top: 2% !important;
      }
      
      #anim4 {
        max-width: 40% !important;
        margin-top: 2% !important;
      }
      
      body {
        overflow-x: hidden !important;
      }
    }
  </style>
</svelte:head>

<!-- Видео фон -->
<video class="background-video" autoplay muted loop playsinline webkit-playsinline>
  <source src="/Background.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>

<!-- Контейнер для всех элементов -->
<div class="main-container">
  <!-- Логотип над анимациями -->
  <img 
    src={currentLogo} 
    class="top-video" 
    alt="Logo" 
    on:click={toggleLogo}
  />
  
  <!-- Анимации с Svelte переходами -->
  {#if visibleAnimations.anim1}
    <img 
      src="/1/BIRD.webp" 
      class="anim visible" 
      id="anim1" 
      alt="BIRD"
      in:fade={{ duration: 1000 }}
    />
  {/if}
  
  {#if visibleAnimations.anim2}
    <img 
      src="/1/BGC.webp" 
      class="anim visible" 
      id="anim2" 
      alt="BGC"
      in:fade={{ duration: 1000 }}
    />
  {/if}
  
  {#if visibleAnimations.anim3}
    <img 
      src="/1/ABOUT.webp" 
      class="anim visible" 
      id="anim3" 
      alt="ABOUT"
      in:fade={{ duration: 1000 }}
    />
  {/if}
  
  {#if visibleAnimations.anim4}
    <img 
      src="/1/CONTACT.webp" 
      class="anim visible" 
      id="anim4" 
      alt="CONTACT"
      in:fade={{ duration: 1000 }}
    />
  {/if}
</div> 