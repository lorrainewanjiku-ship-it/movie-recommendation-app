<script>
 
  // Structured movie database with genres
  let movieDatabase = [
    { title: "The Shawshank Redemption", genre: "drama", mood: "inspiring" },
    { title: "Inception", genre: "sci-fi", mood: "mind-bending" },
    { title: "The Grand Budapest Hotel", genre: "comedy", mood: "whimsical" },
    { title: "Parasite", genre: "thriller", mood: "intense" },
    { title: "Spirited Away", genre: "animation", mood: "magical" },
    { title: "The Dark Knight", genre: "action", mood: "intense" },
    { title: "Pulp Fiction", genre: "crime", mood: "intense" },
    { title: "Your Name", genre: "animation", mood: "romantic" },
    { title: "Forrest Gump", genre: "drama", mood: "inspiring" },
    { title: "Interstellar", genre: "sci-fi", mood: "mind-bending" },
    { title: "The Grand Budapest Hotel", genre: "comedy", mood: "whimsical" },
    { title: "Get Out", genre: "thriller", mood: "intense" },
    { title: "Toy Story", genre: "animation", mood: "magical" },
    { title: "Mad Max: Fury Road", genre: "action", mood: "intense" },
    { title: "The Notebook", genre: "romance", mood: "romantic" },  // ← Added comma here!
    // NEW MOVIES - Add these:
    { title: "The Bourne Legacy", genre: "action", mood: "intense" },
    { title: "The Bourne Identity", genre: "action", mood: "intense" },
    { title: "Mission Impossible", genre: "action", mood: "intense" },
    { title: "James Bond: Skyfall", genre: "action", mood: "intense" },
    { title: "John Wick", genre: "action", mood: "intense" },
    { title: "Die Hard", genre: "action", mood: "intense" }
  ];


  let userMovie = "";
  let recommendation = "";
  let randomRecommendation = "";

  // Function to get a random movie
  function getRandomMovie() {
    let randomIndex = Math.floor(Math.random() * movieDatabase.length);
    randomRecommendation = movieDatabase[randomIndex].title;
    recommendation = ""; // Clear the similar movie recommendation
  }

  // Function to find similar movies
  function findSimilarMovie() {
    if (!userMovie.trim()) {
      recommendation = "Please enter a movie title!";
      return;
    }

    // Find the movie user entered
    let foundMovie = movieDatabase.find(
      movie => movie.title.toLowerCase().includes(userMovie.toLowerCase())
    );

    if (foundMovie) {
      // Find movies with same genre or mood
      let similarMovies = movieDatabase.filter(
        movie => 
          (movie.genre === foundMovie.genre || movie.mood === foundMovie.mood) &&
          movie.title !== foundMovie.title
      );

      if (similarMovies.length > 0) {
        let randomIndex = Math.floor(Math.random() * similarMovies.length);
        recommendation = `Since you liked "${foundMovie.title}", you might enjoy "${similarMovies[randomIndex].title}"!`;
      } else {
        recommendation = `We found "${foundMovie.title}" but couldn't find similar movies. Try our random recommendation!`;
      }
    } else {
      recommendation = `We couldn't find "${userMovie}" in our database. Try our random recommendation!`;
    }

    randomRecommendation = ""; // Clear random recommendation
  }
</script>

<main>
  <h1>🎬 Movie Recommendation Helper</h1>
  <p>Not sure what to watch? Let me help!</p>
  
  <!-- Random Recommendation Section -->
  <div class="section">
    <h3>Get a Random Recommendation</h3>
    <button on:click={getRandomMovie}>Surprise Me!</button>
    
    {#if randomRecommendation}
      <div class="recommendation">
        <h2>You should watch:</h2>
        <p>{randomRecommendation}</p>
      </div>
    {/if}
  </div>

  <div class="divider">OR</div>

  <!-- Similar Movie Section -->
  <div class="section">
    <h3>Find Similar Movies</h3>
    <input 
      type="text" 
      bind:value={userMovie} 
      placeholder="Enter a movie you liked..."
      on:keypress={(e) => e.key === 'Enter' && findSimilarMovie()}
    />
    <button on:click={findSimilarMovie}>Find Similar</button>
    
    {#if recommendation}
      <div class="recommendation">
        <p>{recommendation}</p>
      </div>
    {/if}
  </div>
</main>

<style>
  main {
    text-align: center;
    padding: 2rem;
    max-width: 700px;
    margin: 0 auto;
    font-family: Arial, sans-serif;
  }

  h1 {
    color: #ff3e00;
    font-size: 2.5rem;
    margin-bottom: 1rem;
  }

  p {
    font-size: 1.2rem;
    color: #666;
  }

  .section {
    margin: 2rem 0;
    padding: 1.5rem;
    background-color: #f9f9f9;
    border-radius: 12px;
  }

  h3 {
    color: #333;
    margin-bottom: 1rem;
  }

  input {
    width: 80%;
    padding: 0.8rem;
    font-size: 1rem;
    border: 2px solid #ddd;
    border-radius: 8px;
    margin-bottom: 1rem;
  }

  input:focus {
    outline: none;
    border-color: #ff3e00;
  }

  button {
    background-color: #ff3e00;
    color: white;
    border: none;
    padding: 1rem 2rem;
    font-size: 1.1rem;
    border-radius: 8px;
    cursor: pointer;
    margin: 0.5rem;
  }

  button:hover {
    background-color: #e63900;
  }

  .divider {
    font-size: 1.5rem;
    font-weight: bold;
    color: #999;
    margin: 2rem 0;
  }

  .recommendation {
    background-color: #fff;
    padding: 1.5rem;
    border-radius: 12px;
    margin-top: 1rem;
    box-shadow: 0 2px 8px rgba(0,0,0,0.1);
    animation: fadeIn 0.5s;
  }

  .recommendation h2 {
    color: #333;
    margin-bottom: 0.5rem;
  }

  .recommendation p {
    color: #555;
    font-size: 1.1rem;
  }

  @keyframes fadeIn {
    from { opacity: 0; transform: translateY(-10px); }
    to { opacity: 1; transform: translateY(0); }
  }
</style>