<script>
	import ProjectCard from './ProjectCard.svelte';
  
	const projects = [
	  // Add your project details here
	  { title: 'Project 1', description: 'Brief description of Project 1', link: 'https://example.com/project1', imageUrl: 'https://azsqr-kyaaa-aaaag-qkc5q-cai.raw.icp0.io/?asset=otherImages_collectionImage' },
	  { title: 'Project 2', description: 'Brief description of Project 2', link: 'https://example.com/project2', imageUrl: 'https://g3yn2-gaaaa-aaaag-qkcla-cai.raw.icp0.io/?asset=otherImages_collectionImage' },
	  { title: 'Project 3', description: 'Brief description of Project 3', link: 'https://example.com/project3', imageUrl: 'https://h4gro-4aaaa-aaaag-qczsq-cai.raw.icp0.io/?asset=otherImages_collectionImage' },
	  { title: 'Project 4', description: 'Brief description of Project 4', link: 'https://example.com/project4', imageUrl: 'https://lnu2v-eyaaa-aaaag-qcy4a-cai.raw.icp0.io/?asset=otherImages_collectionImage' },
	  { title: 'Project 5', description: 'Brief description of Project 5', link: 'https://example.com/project5', imageUrl: 'https://3l372-hyaaa-aaaag-qcpfa-cai.raw.icp0.io/?asset=otherImages_collectionImage' },
	  { title: 'Project 6', description: 'Brief description of Project 6', link: 'https://example.com/project6', imageUrl: 'https://kijvo-fqaaa-aaaag-qb4ea-cai.raw.ic0.app/?asset=otherImages_collectionImage' },
	  { title: 'Project 7', description: 'Brief description of Project 7', link: 'https://example.com/project7', imageUrl: 'https://gn5hc-liaaa-aaaag-qbj5q-cai.raw.ic0.app/?asset=otherImages_collectionImage' },
	  { title: 'Project 8', description: 'Brief description of Project 8', link: 'https://example.com/project8', imageUrl: 'https://t3lq2-raaaa-aaaag-qbswa-cai.raw.ic0.app/?asset=otherImages_collectionImage' },
	  { title: 'Project 9', description: 'Brief description of Project 9', link: 'https://example.com/project9', imageUrl: 'https://via.placeholder.com/300x200' },
	  { title: 'Project 10', description: 'Brief description of Project 10', link: 'https://example.com/project10', imageUrl: 'https://via.placeholder.com/300x200' },
	  { title: 'Project 11', description: 'Brief description of Project 11', link: 'https://example.com/project11', imageUrl: 'https://via.placeholder.com/300x200' },
	  { title: 'Project 12', description: 'Brief description of Project 12', link: 'https://example.com/project12', imageUrl: 'https://via.placeholder.com/300x200' },
	  // Add more projects as needed
	];
  </script>
  
  <main>
	<header>
	  <h1>AIMSOMNIA</h1>
	  <h2>Web3 NFT Creator</h2>
	</header>
  
	<section class="project-grid">
	  {#each projects as project}
		<ProjectCard {project} />
	  {/each}
	</section>
  
	<footer class="centered-footer">
	  <p>Follow me on:</p>
	  <a href="https://twitter.com/aimsomnia" target="_blank" rel="noopener noreferrer">Twitter/X</a>
	</footer>
  </main>
  
  <style>
	:global(body) {
	  margin: 0;
	  padding: 0;
	  background-color: black;
	  color: white;
	  font-family: 'Space Mono', monospace;
	}
  
	main {
	  max-width: 1200px;
	  margin: 0 auto;
	  padding: 2rem;
	}
  
	header {
	  text-align: center;
	  margin-bottom: 3rem;
	}
  
	h1 {
	  font-size: 3rem;
	  font-weight: 700;
	  margin: 0;
	  text-transform: uppercase;
	}
  
	h2 {
	  font-size: 1.5rem;
	  font-weight: 400;
	  margin: 0.5rem 0 0;
	  opacity: 0.8;
	}
  
	.project-grid {
	  display: grid;
	  grid-template-columns: repeat(4, 1fr);
	  grid-gap: 2rem;
	  margin-bottom: 3rem;
	}
  
	.centered-footer {
	  text-align: center;
	  padding: 2rem 0;
	  border-top: 1px solid white;
	}
  
	a {
	  color: white;
	  text-decoration: none;
	  font-weight: 700;
	}
  
	a:hover {
	  text-decoration: underline;
	}
  
	/* Responsive styles */
	@media (max-width: 768px) {
	  .project-grid {
		grid-template-columns: repeat(2, 1fr);
	  }
	}
  
	@media (max-width: 480px) {
	  h1 {
		font-size: 2rem;
	  }
  
	  h2 {
		font-size: 1.2rem;
	  }
  
	  .project-grid {
		grid-template-columns: 1fr;
	  }
	}
  </style>