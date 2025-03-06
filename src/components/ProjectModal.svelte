<script>
    import { createEventDispatcher } from 'svelte';
    
    // Props
    export let project;
    export let isOpen = false;
    
    // Event dispatcher
    const dispatch = createEventDispatcher();
    
    // Close modal
    function closeModal() {
      dispatch('close');
    }
    
    // Handle key press
    function handleKeydown(event) {
      if (event.key === 'Escape') {
        closeModal();
      }
    }
    
    // Handle click outside
    function handleOutsideClick(event) {
      if (event.target === event.currentTarget) {
        closeModal();
      }
    }
  </script>
  
  <svelte:window on:keydown={handleKeydown} />
  
  {#if isOpen}
    <div 
      class="modal-overlay" 
      on:click={handleOutsideClick}
      on:keydown={handleKeydown}
      tabindex="0"
      role="button"
      aria-label="Close modal">
      <div class="modal-content" role="dialog" aria-modal="true" aria-labelledby="modal-title">
        <button class="close-button" on:click={closeModal} aria-label="Close modal">×</button>
        
        <div class="modal-image">
          <img src={project.imageUrl} alt={project.title} />
        </div>
        
        <div class="modal-details">
          <h2 id="modal-title">{project.title}</h2>
          
          <p class="project-description">{project.description}</p>
          
          <div class="project-meta">
            <div class="meta-item">
              <h3>Year</h3>
              <p>{project.year}</p>
            </div>
            
            <div class="meta-item">
              <h3>Technologies</h3>
              <div class="tech-tags">
                {#each project.technologies as tech}
                  <span class="tech-tag">{tech}</span>
                {/each}
              </div>
            </div>
          </div>
          
          <a href={project.link} class="project-link" target="_blank" rel="noopener noreferrer">
            View Project
          </a>
        </div>
      </div>
    </div>
  {/if}
  
  <style>
    .modal-overlay {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background-color: rgba(0, 0, 0, 0.9);
      display: flex;
      align-items: center;
      justify-content: center;
      z-index: 1000;
      padding: 2rem;
      backdrop-filter: blur(5px);
    }
    
    .modal-content {
      background-color: #111;
      border: 1px solid #333;
      border-radius: 4px;
      max-width: 1000px;
      width: 100%;
      max-height: 90vh;
      overflow-y: auto;
      position: relative;
      display: grid;
      grid-template-columns: 1fr 1fr;
      animation: fadeIn 0.3s ease;
    }
    
    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(20px); }
      to { opacity: 1; transform: translateY(0); }
    }
    
    .close-button {
      position: absolute;
      top: 1rem;
      right: 1rem;
      background: none;
      border: none;
      color: white;
      font-size: 2rem;
      cursor: pointer;
      z-index: 10;
      width: 40px;
      height: 40px;
      display: flex;
      align-items: center;
      justify-content: center;
      border-radius: 50%;
      background-color: rgba(0, 0, 0, 0.5);
      transition: background-color 0.3s ease;
    }
    
    .close-button:hover {
      background-color: rgba(255, 255, 255, 0.1);
    }
    
    .modal-image {
      height: 100%;
      overflow: hidden;
    }
    
    .modal-image img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }
    
    .modal-details {
      padding: 2rem;
      display: flex;
      flex-direction: column;
    }
    
    h2 {
      font-size: 2rem;
      margin: 0 0 1rem;
    }
    
    .project-description {
      margin-bottom: 2rem;
      line-height: 1.7;
    }
    
    .project-meta {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 2rem;
      margin-bottom: 2rem;
    }
    
    .meta-item h3 {
      font-size: 1rem;
      margin: 0 0 0.5rem;
      opacity: 0.7;
    }
    
    .tech-tags {
      display: flex;
      flex-wrap: wrap;
      gap: 0.5rem;
    }
    
    .tech-tag {
      font-size: 0.8rem;
      background-color: #222;
      padding: 0.3rem 0.7rem;
      border-radius: 2px;
      border: 1px solid #444;
    }
    
    .project-link {
      display: inline-block;
      padding: 1rem 2rem;
      background-color: white;
      color: black;
      text-align: center;
      font-weight: 700;
      border-radius: 4px;
      margin-top: auto;
      transition: transform 0.3s ease, opacity 0.3s ease;
    }
    
    .project-link:hover {
      transform: translateY(-3px);
      opacity: 0.9;
    }
    
    @media (max-width: 768px) {
      .modal-content {
        grid-template-columns: 1fr;
      }
      
      .modal-image {
        height: 300px;
      }
    }
    
    @media (max-width: 480px) {
      .modal-overlay {
        padding: 1rem;
      }
      
      .modal-details {
        padding: 1.5rem;
      }
      
      .project-meta {
        grid-template-columns: 1fr;
        gap: 1rem;
      }
    }
  </style>