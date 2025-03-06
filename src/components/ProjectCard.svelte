<script>
  import { createEventDispatcher } from 'svelte';
  
  export let project;
  
  // Track image loading state
  let imageLoaded = false;
  
  // Event dispatcher
  const dispatch = createEventDispatcher();
  
  // Handle image load event
  function handleImageLoad() {
    imageLoaded = true;
  }
  
  // Handle card click to open modal
  function openProjectDetails() {
    dispatch('openModal', project);
  }
</script>

<div class="card" on:click={openProjectDetails} on:keydown={(e) => e.key === 'Enter' && openProjectDetails()} tabindex="0" role="button" aria-label={`View details of ${project.title}`}>
  <div class="image-container">
    <div class="image-placeholder" class:hidden={imageLoaded}></div>
    <img 
      src={project.imageUrl} 
      alt={project.title} 
      class="card-image" 
      class:loaded={imageLoaded}
      loading="lazy" 
      on:load={handleImageLoad} 
    />
  </div>
  <div class="card-content">
    <h3>{project.title}</h3>
    <p class="description">{project.description}</p>
    <div class="meta">
      <span class="year">{project.year}</span>
      <div class="tech-tags">
        {#each project.technologies.slice(0, 2) as tech}
          <span class="tech-tag">{tech}</span>
        {/each}
        {#if project.technologies.length > 2}
          <span class="tech-tag">+{project.technologies.length - 2}</span>
        {/if}
      </div>
    </div>
  </div>
</div>

<style>
  .card {
    background-color: #111;
    border: 1px solid #333;
    border-radius: 4px;
    overflow: hidden;
    transition: transform 0.3s ease, border-color 0.3s ease, box-shadow 0.3s ease;
    height: 100%;
    display: flex;
    flex-direction: column;
    cursor: pointer;
  }

  .card:hover {
    transform: translateY(-5px);
    border-color: white;
    box-shadow: 0 5px 15px rgba(255, 255, 255, 0.1);
  }
  
  .card:focus {
    outline: 2px solid white;
    outline-offset: 2px;
  }
  
  .image-container {
    position: relative;
    width: 100%;
    height: 200px;
    overflow: hidden;
  }
  
  .image-placeholder {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: linear-gradient(110deg, #111 8%, #222 18%, #111 33%);
    background-size: 200% 100%;
    animation: 1.5s shine linear infinite;
  }
  
  .image-placeholder.hidden {
    opacity: 0;
  }
  
  @keyframes shine {
    to {
      background-position-x: -200%;
    }
  }

  .card-image {
    width: 100%;
    height: 100%;
    object-fit: cover;
    border-bottom: 1px solid #333;
    transition: opacity 0.3s ease, transform 0.5s ease;
    opacity: 0;
  }
  
  .card-image.loaded {
    opacity: 1;
  }
  
  .card:hover .card-image.loaded {
    transform: scale(1.05);
  }

  .card-content {
    padding: 1.5rem;
    flex-grow: 1;
    display: flex;
    flex-direction: column;
  }

  h3 {
    margin: 0 0 0.5rem;
    font-size: 1.2rem;
    font-weight: 700;
  }

  .description {
    margin: 0 0 1rem;
    font-size: 0.9rem;
    opacity: 0.8;
    line-height: 1.4;
    flex-grow: 1;
    
    /* Limit to 3 lines with ellipsis */
    display: -webkit-box;
    -webkit-line-clamp: 3;
    -webkit-box-orient: vertical;
    overflow: hidden;
  }
  
  .meta {
    display: flex;
    flex-direction: column;
    gap: 0.5rem;
    margin-top: auto;
  }
  
  .year {
    font-size: 0.8rem;
    opacity: 0.6;
  }

  .tech-tags {
    display: flex;
    flex-wrap: wrap;
    gap: 0.5rem;
  }
  
  .tech-tag {
    font-size: 0.7rem;
    background-color: #222;
    padding: 0.2rem 0.5rem;
    border-radius: 2px;
    border: 1px solid #444;
  }

  @media (max-width: 768px) {
    .image-container {
      height: 150px;
    }
  }

  @media (max-width: 480px) {
    .image-container {
      height: 120px;
    }
  }
</style>