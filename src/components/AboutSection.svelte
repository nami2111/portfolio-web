<script>
  // You can add props here if needed
</script>

<section class="about">
  <h2>About Me</h2>
  
  <div class="about-content">
    <div class="about-text">
      <p>
        I'm a Web3 NFT creator passionate about exploring the possibilities of blockchain technology in digital art.
      </p>
      
      <p>
        I'm constantly experimenting and learning with new techniques and platforms to push the boundaries of what's possible in the NFT space.
      </p>
      
      <h3>My Approach</h3>
      <p>
        I believe in the power of blockchain to revolutionize how we create, share, and value digital art.
      </p>
    </div>
  </div>
</section>

<style>
  .about {
    max-width: 1000px;
    margin: 5rem auto;
    padding: 2rem;
    background-color: #111;
    border: 1px solid #333;
    border-radius: 4px;
  }
  
  h2 {
    text-align: center;
    margin-bottom: 2rem;
    font-size: 2rem;
    position: relative;
  }
  
  h2:after {
    content: "";
    display: block;
    width: 50px;
    height: 2px;
    background-color: white;
    margin: 1rem auto 0;
  }
  
  h3 {
    margin: 1.5rem 0 1rem;
    font-size: 1.3rem;
  }
  
  .about-content {
    display: flex;
    justify-content: center;
  }
  
  .about-text {
    max-width: 700px;
  }
  
  .about-text p {
    margin-bottom: 1rem;
    line-height: 1.7;
  }
  
  @media (max-width: 768px) {
    .about {
      padding: 1.5rem;
    }
  }
</style>