<script>
    export let project;
  </script>
  
  <a href={project.link} target="_blank" rel="noopener noreferrer">
    <div class="card">
      <img src={project.imageUrl} alt={project.title} class="card-image" />
      <div class="card-content">
        <h3>{project.title}</h3>
        <p>{project.description}</p>
      </div>
    </div>
  </a>
  
  <style>
    .card {
      background-color: #111;
      border: 1px solid #333;
      border-radius: 4px;
      overflow: hidden;
      transition: transform 0.2s ease, border-color 0.2s ease;
    }
  
    .card:hover {
      transform: translateY(-5px);
      border-color: white;
    }
  
    .card-image {
      width: 100%;
      height: 200px;
      object-fit: cover;
      border-bottom: 1px solid #333;
    }
  
    .card-content {
      padding: 1.5rem;
    }
  
    h3 {
      margin: 0 0 0.5rem;
      font-size: 1.2rem;
      font-weight: 700;
    }
  
    p {
      margin: 0;
      font-size: 0.9rem;
      opacity: 0.8;
      line-height: 1.4;
    }
  
    @media (max-width: 768px) {
      .card-image {
        height: 150px;
      }
    }
  
    @media (max-width: 480px) {
      .card-image {
        height: 120px;
      }
    }
  </style>