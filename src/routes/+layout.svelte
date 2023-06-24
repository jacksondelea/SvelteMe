<script>
    import { onMount } from 'svelte';
    
    onMount(() => {
      document.body.style.backgroundColor = '#d8d8d8';
      document.body.style.fontFamily = '-Eurostile';
      document.body.style.color = 'black';
    });
  </script>
  
  <slot />
  