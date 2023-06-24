<script>
    import { onMount } from 'svelte';
    let light = false;
    
    // Check for saved theme preference on mount
    onMount(() => {
      if (window.matchMedia && window.matchMedia('(prefers-color-scheme: light)').matches) {
        light = true;
      }
    });
  
    // Update theme when button is clicked
    function toggleTheme() {
      light = !light;
      document.body.setAttribute('data-theme', light ? 'dark' : 'light');
    }
  </script>
  
  <span on:click={toggleTheme}>
    + / -
  </span>

  <style>
    span{
        cursor: pointer;
    }
  </style>
  