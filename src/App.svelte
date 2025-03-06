<script>
	import ProjectCard from './components/ProjectCard.svelte';
	import AboutSection from './components/AboutSection.svelte';
	import HeroSection from './components/HeroSection.svelte';
	import ProjectModal from './components/ProjectModal.svelte';
	import { projects } from './data/projects.js';
	
	// State for filtering projects
	let selectedYear = 'all';
	let searchQuery = '';
	let selectedTechnology = 'all';
	
	// State for project modal
	let selectedProject = null;
	let isModalOpen = false;
	
	// Get unique years and technologies for filter dropdowns
	$: years = [...new Set(projects.map(project => project.year))].sort((a, b) => b - a);
	$: technologies = [...new Set(projects.flatMap(project => project.technologies))].sort();
	
	// Computed property for filtered projects
	$: filteredProjects = projects.filter(project => {
	  // Filter by year if a specific year is selected
	  const yearMatch = selectedYear === 'all' || project.year.toString() === selectedYear;
	  
	  // Filter by technology if a specific technology is selected
	  const techMatch = selectedTechnology === 'all' || 
					   project.technologies.includes(selectedTechnology);
	  
	  // Filter by search query (case insensitive)
	  const searchMatch = searchQuery === '' ||
		project.title.toLowerCase().includes(searchQuery.toLowerCase()) ||
		project.description.toLowerCase().includes(searchQuery.toLowerCase()) ||
		project.technologies.some(tech => 
		  tech.toLowerCase().includes(searchQuery.toLowerCase())
		);
	  
	  return yearMatch && techMatch && searchMatch;
	});
	
	// Scroll to section
	function scrollToSection(id) {
	  const element = document.getElementById(id);
	  if (element) {
		element.scrollIntoView({ behavior: 'smooth' });
	  }
	}
	
	// Open project modal
	function openProjectModal(event) {
	  selectedProject = event.detail;
	  isModalOpen = true;
	  // Prevent scrolling when modal is open
	  document.body.style.overflow = 'hidden';
	}
	
	// Close project modal
	function closeProjectModal() {
	  isModalOpen = false;
	  // Re-enable scrolling
	  document.body.style.overflow = '';
	}
</script>
  
<header class="main-header">
  <div class="logo">AIMSOMNIA</div>
  <nav class="main-nav">
    <ul>
      <li><button on:click={() => scrollToSection('projects')}>Projects</button></li>
      <li><button on:click={() => scrollToSection('about')}>About</button></li>
    </ul>
  </nav>
</header>
  
<HeroSection />
  
<main>
  <section class="projects" id="projects">
    <h2>My Projects</h2>
    
    <div class="filters">
      <div class="filter-container">
        <div class="search-box">
          <input 
            type="text" 
            placeholder="Search projects..." 
            bind:value={searchQuery}
            aria-label="Search projects"
          />
        </div>
        
        <div class="filter-selects">
          <div class="filter-select">
            <label for="year-select">Year:</label>
            <select id="year-select" bind:value={selectedYear} aria-label="Filter by year">
              <option value="all">All Years</option>
              {#each years as year}
                <option value={year}>{year}</option>
              {/each}
            </select>
          </div>
          
          <div class="filter-select">
            <label for="tech-select">Technology:</label>
            <select id="tech-select" bind:value={selectedTechnology} aria-label="Filter by technology">
              <option value="all">All Technologies</option>
              {#each technologies as tech}
                <option value={tech}>{tech}</option>
              {/each}
            </select>
          </div>
        </div>
      </div>
      
      {#if filteredProjects.length === 0}
        <p class="no-results">No projects match your search criteria.</p>
      {/if}
    </div>

    <div class="project-grid">
      {#each filteredProjects as project (project.id)}
        <ProjectCard {project} on:openModal={openProjectModal} />
      {/each}
    </div>
  </section>

  <div id="about">
    <AboutSection />
  </div>

  <footer class="centered-footer">
    <div class="social-links">
      <a href="https://twitter.com/aimsomnia" target="_blank" rel="noopener noreferrer" aria-label="Twitter profile">Twitter/X</a>
      <a href="https://instagram.com/aimsomnia" target="_blank" rel="noopener noreferrer" aria-label="Instagram profile">Instagram</a>
      <a href="https://opensea.io/aimsomnia" target="_blank" rel="noopener noreferrer" aria-label="OpenSea profile">OpenSea</a>
      <a href="https://foundation.app/aimsomnia" target="_blank" rel="noopener noreferrer" aria-label="Foundation profile">Foundation</a>
    </div>
    <p class="copyright">© {new Date().getFullYear()} AIMSOMNIA. All rights reserved.</p>
  </footer>
</main>
  
{#if selectedProject}
  <ProjectModal 
    project={selectedProject} 
    isOpen={isModalOpen} 
    on:close={closeProjectModal} 
  />
{/if}
  
<style>
  :global(body) {
    margin: 0;
    padding: 0;
    background-color: black;
    color: white;
    font-family: 'Space Mono', monospace;
    overflow-x: hidden;
  }
  
  .main-header {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1.5rem 2rem;
    z-index: 100;
    background-color: rgba(0, 0, 0, 0.8);
    backdrop-filter: blur(10px);
  }
  
  .logo {
    font-size: 1.5rem;
    font-weight: 700;
    text-transform: uppercase;
    letter-spacing: 0.1em;
  }
  
  .main-nav ul {
    display: flex;
    gap: 2rem;
    list-style: none;
    padding: 0;
    margin: 0;
  }
  
  .main-nav button {
    background: none;
    border: none;
    color: white;
    font-size: 1rem;
    cursor: pointer;
    padding: 0.5rem 0;
    transition: opacity 0.2s ease;
    position: relative;
  }
  
  .main-nav button:after {
    content: '';
    position: absolute;
    width: 0;
    height: 2px;
    bottom: 0;
    left: 50%;
    background-color: white;
    transition: all 0.3s ease;
  }
  
  .main-nav button:hover:after {
    width: 100%;
    left: 0;
  }

  main {
    max-width: 1200px;
    margin: 0 auto;
    padding: 2rem;
  }
  
  .projects {
    margin: 5rem 0;
  }
  
  .projects h2 {
    text-align: center;
    margin-bottom: 2rem;
    font-size: 2rem;
    position: relative;
  }
  
  .projects h2:after {
    content: "";
    display: block;
    width: 50px;
    height: 2px;
    background-color: white;
    margin: 1rem auto 0;
  }
  
  .filters {
    margin-bottom: 2rem;
  }
  
  .filter-container {
    display: flex;
    flex-direction: column;
    gap: 1rem;
    background-color: #111;
    padding: 1.5rem;
    border-radius: 4px;
    border: 1px solid #333;
  }
  
  .search-box input {
    padding: 0.8rem 1rem;
    background-color: #222;
    border: 1px solid #333;
    color: white;
    border-radius: 4px;
    width: 100%;
    font-family: 'Space Mono', monospace;
  }
  
  .filter-selects {
    display: flex;
    gap: 1rem;
    flex-wrap: wrap;
  }
  
  .filter-select {
    display: flex;
    align-items: center;
    gap: 0.5rem;
    flex: 1;
    min-width: 200px;
  }
  
  .filter-select select {
    padding: 0.5rem 1rem;
    background-color: #222;
    border: 1px solid #333;
    color: white;
    border-radius: 4px;
    flex: 1;
    font-family: 'Space Mono', monospace;
  }
  
  .no-results {
    text-align: center;
    margin: 2rem 0;
    font-style: italic;
    padding: 2rem;
    background-color: #111;
    border: 1px solid #333;
    border-radius: 4px;
  }

  .project-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
    grid-gap: 2rem;
    margin-bottom: 3rem;
  }
  
  .centered-footer {
    text-align: center;
    padding: 2rem 0;
    border-top: 1px solid #333;
    margin-top: 4rem;
  }
  
  .social-links {
    display: flex;
    justify-content: center;
    gap: 2rem;
    margin-bottom: 1rem;
    flex-wrap: wrap;
  }

  a {
    color: white;
    text-decoration: none;
    font-weight: 700;
    transition: opacity 0.2s ease;
  }

  a:hover {
    opacity: 0.7;
  }
  
  .copyright {
    font-size: 0.8rem;
    opacity: 0.6;
  }

  /* Responsive styles */
  @media (max-width: 1024px) {
    .project-grid {
      grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
    }
  }
  
  @media (max-width: 768px) {
    .main-header {
      flex-direction: column;
      padding: 1rem;
    }
    
    .logo {
      margin-bottom: 1rem;
    }
    
    .main-nav ul {
      gap: 1rem;
    }
    
    .filter-container {
      flex-direction: column;
      align-items: stretch;
    }
    
    .filter-selects {
      flex-direction: column;
    }
    
    .filter-select {
      width: 100%;
    }
  }

  @media (max-width: 480px) {
    .main-nav ul {
      flex-direction: column;
      gap: 0.5rem;
      align-items: center;
    }
    
    .social-links {
      gap: 1rem;
      flex-direction: column;
    }
  }
</style>