# Getting Started with Svelte – A Beginner's Guide

## 1. Title & Objective

**Technology Chosen:** Svelte

**Why I chose it:** I wanted to learn a frontend framework that would allow me to create visual, interactive web applications. Svelte appealed to me because it's beginner-friendly and I could see my work come to life in the browser, making it easier to understand what I'm building.

**End Goal:** Create a simple interactive movie recommendation web app that displays random movie suggestions and finds similar movies based on user input.

---

## 2. Quick Summary of the Technology

**What is Svelte?**
Svelte is a modern frontend framework for building web applications. Unlike other frameworks like React or Vue, Svelte compiles your code at build time, resulting in faster and smaller applications.

**Where is it used?**
Svelte is used for building interactive web applications, single-page applications (SPAs), and user interfaces.

**Real-world example:**
Companies like The New York Times, Apple, and Spotify use Svelte for parts of their web applications.

---

## 3. System Requirements

**Operating System:** Windows 10/11 (works on Mac/Linux too)

**Tools Required:**
- **VS Code** - Code editor
- **Node.js** (v20 or higher) - JavaScript runtime
- **Git** - Version control
- **Web Browser** - Chrome, Edge, Firefox, etc.

**Package Manager:** npm (comes with Node.js)

---

## 4. Installation & Setup Instructions

### Step 1: Install Node.js

1. Go to https://nodejs.org/
2. Download the LTS version
3. Run the installer and follow the prompts
4. Verify installation by opening Command Prompt and typing:
```
   node --version
   npm --version
```

### Step 2: Create a Svelte Project

1. Open Command Prompt
2. Navigate to where you want to create your project:
```
   cd C:\Users\YourName
```
3. Create a new Svelte project:
```
   npm create vite@latest my-svelte-app -- --template svelte
```
4. Select "No" for experimental features
5. Select "Yes" to install and start

### Step 3: Navigate and Install
```
cd my-svelte-app
npm install
```

### Step 4: Start Development Server
```
npm run dev
```

Your app will be available at: http://localhost:5173/

### Step 5: Open in VS Code
```
code .
```

---

## 5. Building the Movie Recommendation App

### Overview
The app has two main features:
1. **Random Recommendation:** Click a button to get a surprise movie suggestion
2. **Similar Movie Finder:** Type a movie you've watched and get similar recommendations based on genre and mood

### Key Concepts Used
- **Reactive variables:** Variables that automatically update the UI when changed
- **Event handling:** Responding to button clicks and keyboard input
- **Conditional rendering:** Showing/hiding content based on conditions
- **Array methods:** Searching and filtering data

---

## 6. AI Prompt Journal

### Prompt 1: Basic Setup
**Prompt used:** "How do I replace the counter app in App.svelte with a simple welcome message that says 'Movie Recommendation Helper'?"

**AI's response summary:** The AI explained that Svelte components have three sections (script, HTML, style) and showed me how to remove the default counter code and add a simple welcome message with a button.

**What I learned:** Svelte files are organized into script, HTML template, and style sections. I can easily modify the HTML section to change what appears on the page.

**Evaluation:** Very helpful - gave me a clear understanding of Svelte's structure.
**Note:** The ai.moringaschool.com platform was restricted to organization members only and I could not access it. Instead, I used Claude AI (claude.ai) as my AI assistant for this project, which provided equivalent learning support through conversational prompts.
---

### Prompt 2: Adding Interactivity
**Prompt used:** "How do I make the button show a random movie recommendation when clicked?"

**AI's response summary:** The AI showed me how to:
- Create an array of movies
- Write a function to pick random movies
- Use `on:click` to connect the button to the function
- Use `{#if}` for conditional rendering
- Display the recommendation

**What I learned:** 
- Svelte uses `on:click={functionName}` for event handling
- Variables can be displayed using `{variableName}`
- Conditional rendering uses `{#if condition}...{/if}` blocks
- `Math.random()` and `Math.floor()` help generate random numbers

**Evaluation:** Extremely helpful - introduced me to Svelte's reactivity and event handling.

---

### Prompt 3: Adding User Input Feature
**Prompt used:** "How can I add a text input where users can type a movie they've watched, and then suggest similar movies based on genre or mood?"

**AI's response summary:** The AI showed me how to:
- Restructure the movie data to include genre and mood properties
- Create an input field using `<input>` with two-way binding (`bind:value`)
- Write a function to search for movies and find similar ones based on genre/mood
- Use `.find()` and `.filter()` methods to search through arrays
- Handle cases where the movie isn't found in the database
- Allow users to press Enter to submit (using `on:keypress`)

**What I learned:**
- **Data structures:** Using objects with properties (title, genre, mood) makes it easier to organize and search data
- **Two-way binding:** `bind:value={userMovie}` automatically updates the variable when the user types
- **Array methods:** `.find()` searches for one item, `.filter()` finds multiple items that match criteria
- **String methods:** `.toLowerCase()` and `.includes()` help match user input even if capitalization is different
- **Conditional logic:** Using `if/else` to handle different scenarios (movie found, not found, no similar movies)

**Evaluation:** Very helpful - introduced me to working with user input, data searching, and more complex JavaScript logic.

---

## 7. Common Issues & Fixes

### Issue 1: PowerShell Script Execution Error
**Error:** `npm.ps1 cannot be loaded because running scripts is disabled`

**Solution:** Use Command Prompt instead of PowerShell, or change PowerShell execution policy

**How I fixed it:** Switched from PowerShell to Command Prompt in VS Code terminal

---

### Issue 2: Double Closing Script Tag
**Error:** `</script> attempted to close an element that was not open`

**Solution:** Check that you only have ONE `<script>` opening tag and ONE `</script>` closing tag

**How I fixed it:** Removed the extra `</script>` tag

---

### Issue 3: npm command not working
**Error:** `Could not read package.json`

**Solution:** Make sure you're in the correct project directory

**How I fixed it:** Used `cd my-svelte-app` to navigate to the project folder

---

### Issue 4: Missing Comma in Array
**Error:** Syntax error when adding new items to the movieDatabase array

**Solution:** Make sure each object in the array has a comma after it (except the last one)

**Example:**
```javascript
// Wrong:
{ title: "Movie 1" }
{ title: "Movie 2" }  // Missing comma above!

// Correct:
{ title: "Movie 1" },  // Comma here
{ title: "Movie 2" }
```

**How I fixed it:** Added a comma after the last movie in the original list before adding new movies

---

## 8. Final Code

### Complete App.svelte
```svelte
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
    { title: "Get Out", genre: "thriller", mood: "intense" },
    { title: "Toy Story", genre: "animation", mood: "magical" },
    { title: "Mad Max: Fury Road", genre: "action", mood: "intense" },
    { title: "The Notebook", genre: "romance", mood: "romantic" },
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
```

**Code Explanation:**

- **Script section:** Contains the movie database with genres/moods, variables for storing recommendations, and two main functions (random recommendation and similar movie finder)
- **HTML section:** Two separate sections - one for random recommendations and one for searching similar movies
- **Style section:** Responsive styling with hover effects, focus states, and fade-in animations

---

## 9. References

- **Official Svelte Documentation:** https://svelte.dev/docs
- **Svelte Tutorial:** https://svelte.dev/tutorial
- **Vite Documentation:** https://vitejs.dev/
- **Node.js:** https://nodejs.org/
- **MDN Web Docs (JavaScript):** https://developer.mozilla.org/en-US/docs/Web/JavaScript

---

## 10. Reflections

### What I Learned

This capstone project was my first experience with web development and frontend frameworks. Before starting, I had no background in software development, so everything from installing Node.js to understanding how Svelte works was completely new to me.

**Key Takeaways:**
- **Svelte's simplicity:** I was surprised by how straightforward Svelte is compared to what I expected. The three-section structure (script, HTML, style) made it easy to understand where different parts of the code belong.
- **Reactivity:** Learning how Svelte automatically updates the page when variables change was eye-opening. I didn't have to manually refresh or update anything.
- **Problem-solving:** I encountered several errors (PowerShell issues, double script tags, wrong directory, missing commas), but working through them taught me to read error messages carefully and use the right tools.
- **AI-assisted learning:** Using AI to guide me through the learning process was incredibly helpful. Instead of feeling overwhelmed by documentation, I could ask specific questions and get targeted answers.

### Challenges Faced

**Technical challenges:**
- Setting up the development environment was initially confusing, especially dealing with PowerShell vs Command Prompt
- Understanding the folder structure and knowing which files to edit took some time
- Learning when to save files and how hot-reloading works in Vite
- Working with JavaScript array methods and understanding data structures

**Learning challenges:**
- Coming from a non-technical background, even basic concepts like "running a development server" were new to me
- Understanding JavaScript syntax within Svelte templates required careful attention
- Debugging syntax errors like missing commas taught me to pay close attention to detail

### What Surprised Me

I was surprised by how quickly I could see results. Within a few hours, I went from having no Svelte knowledge to building a working, interactive web application with multiple features. The instant feedback from the browser made the learning process engaging and rewarding.

### What I Would Do Differently

If I were to start over, I would:
- Take more time to read through the official Svelte tutorial before diving in
- Document my errors and solutions as they happened, rather than trying to remember them later
- Experiment more with different features and styling options
- Set up version control (Git) from the beginning

### Future Improvements

Given more time, I would like to add:
- More comprehensive movie database with additional genres
- User ratings and reviews
- A "watched list" to track movies already seen
- Integration with a real movie API (like TMDB) for actual movie data and posters
- Better mobile responsiveness
- Save user preferences using local storage

### Overall Experience

This project gave me confidence that I can learn new technologies independently with the right guidance. While web development is still new to me, completing this capstone showed me that breaking down complex tasks into smaller steps makes learning manageable and even enjoyable. The combination of hands-on building and AI-assisted learning was an effective approach for someone with no prior coding experience.
### Peer Testing
Due to time constraints, formal peer testing was not conducted. However, the app was tested locally by running it multiple times and verifying both features (random recommendations and similar movie finder) worked correctly.
---

**Project completed by:** Lorraine Wanjiku
**Date:** November 27, 2024
**Technology:** Svelte with Vite
**GitHub Repository:** https://github.com/lorrainewanjiku-ship-it/movie-recommendation-app
