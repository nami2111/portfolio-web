<script>
    import { onMount } from 'svelte';
    
    let isVisible = false;
    
    onMount(() => {
      // Trigger animation after component is mounted
      setTimeout(() => {
        isVisible = true;
      }, 100);
    });
    
    // Function to scroll to projects section
    function scrollToProjects() {
      const projectsSection = document.getElementById('projects');
      if (projectsSection) {
        projectsSection.scrollIntoView({ behavior: 'smooth' });
      }
    }
  </script>
  
  <section class="hero">
    <div class="hero-content" class:visible={isVisible}>
      <h1>AIMSOMNIA</h1>
      <h2>Web3 NFT Creator</h2>
      
      <p class="hero-description">
        Creating unique digital experiences at the intersection of art and blockchain technology.
        Explore my portfolio of NFT collections, interactive experiences, and Web3 projects.
      </p>
      
      <button class="cta-button" on:click={scrollToProjects}>
        View My Work
      </button>
    </div>
    
    <div class="hero-background">
      <div class="grid-line horizontal" style="top: 20%"></div>
      <div class="grid-line horizontal" style="top: 40%"></div>
      <div class="grid-line horizontal" style="top: 60%"></div>
      <div class="grid-line horizontal" style="top: 80%"></div>
      
      <div class="grid-line vertical" style="left: 20%"></div>
      <div class="grid-line vertical" style="left: 40%"></div>
      <div class="grid-line vertical" style="left: 60%"></div>
      <div class="grid-line vertical" style="left: 80%"></div>
    </div>
  </section>
  
  <style>
    .hero {
      position: relative;
      height: 100vh;
      min-height: 600px;
      display: flex;
      align-items: center;
      justify-content: center;
      overflow: hidden;
    }
    
    .hero-content {
      text-align: center;
      z-index: 2;
      opacity: 0;
      transform: translateY(20px);
      transition: opacity 1s ease, transform 1s ease;
      max-width: 800px;
      padding: 0 2rem;
    }
    
    .hero-content.visible {
      opacity: 1;
      transform: translateY(0);
    }
    
    h1 {
      font-size: 4rem;
      font-weight: 700;
      margin: 0;
      text-transform: uppercase;
      letter-spacing: 0.1em;
    }
    
    h2 {
      font-size: 1.8rem;
      font-weight: 400;
      margin: 0.5rem 0 0;
      opacity: 0.8;
    }
    
    .hero-description {
      margin: 2rem auto;
      font-size: 1.2rem;
      line-height: 1.6;
      max-width: 700px;
    }
    
    .cta-button {
      display: inline-block;
      padding: 1rem 2rem;
      background-color: white;
      color: black;
      border: none;
      font-weight: 700;
      font-size: 1rem;
      cursor: pointer;
      transition: transform 0.3s ease, box-shadow 0.3s ease;
      margin-top: 1rem;
    }
    
    .cta-button:hover {
      transform: translateY(-3px);
      box-shadow: 0 5px 15px rgba(255, 255, 255, 0.2);
    }
    
    .hero-background {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      z-index: 1;
    }
    
    .grid-line {
      position: absolute;
      background-color: rgba(255, 255, 255, 0.05);
    }
    
    .horizontal {
      width: 100%;
      height: 1px;
      transform-origin: left;
      animation: scaleIn 2s ease forwards;
    }
    
    .vertical {
      height: 100%;
      width: 1px;
      transform-origin: top;
      animation: scaleIn 2s ease forwards;
    }
    
    @keyframes scaleIn {
      0% {
        transform: scaleX(0);
      }
      100% {
        transform: scaleX(1);
      }
    }
    
    @media (max-width: 768px) {
      h1 {
        font-size: 3rem;
      }
      
      h2 {
        font-size: 1.5rem;
      }
      
      .hero-description {
        font-size: 1rem;
      }
    }
    
    @media (max-width: 480px) {
      h1 {
        font-size: 2.5rem;
      }
      
      h2 {
        font-size: 1.2rem;
      }
      
      .hero {
        min-height: 500px;
      }
    }
  </style>