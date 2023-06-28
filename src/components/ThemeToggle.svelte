<script>
  import { onMount, afterUpdate } from 'svelte';
  
  // Default theme is dark
  let theme = "light";

  // Check for saved theme preference on mount
  onMount(() => {
    if (window.matchMedia && window.matchMedia('(prefers-color-scheme: light)').matches) {
      theme = "light";
    }
    document.body.setAttribute('data-theme', theme);
  });

  // Update theme when button is clicked
  function toggleTheme() {
    theme = theme === "dark" ? "light" : "dark";
    document.body.setAttribute('data-theme', theme);
  }
</script>

<button on:click={toggleTheme}></button>

<style>
  :root {
    --bg-light: #ffffff; /* replace with your light theme color */
    --bg-dark: #121212; /* replace with your dark theme color */
  }

  button {
    cursor: pointer;
    border: none;
    height: 20px;
    width: 20px;
    border-radius: 50%;
  }

  body[data-theme="light"] button {
    background-color: var(--bg-dark);
  }

  body[data-theme="dark"] button {
    background-color: var(--bg-light);
  }
</style>
