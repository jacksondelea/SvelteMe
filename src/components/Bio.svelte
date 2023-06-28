<script>
  import { slide } from 'svelte/transition';

  let expanded = false;
  function toggleBio() {
    expanded = !expanded;
  }

  let shortbio = 'Researcher, writer and designer based in New York City.';
  let extrabio= "I got my B.A. from Brown University, where I studied a mix of literature, computer science, architecture, theory, and design. I'm interested in how technology, politics and culture interact to produce new social conditions. Right now, I'm particularly interested in distributed networks, open source software, and durable interface design. I'm working on developing a critical design practice that connects my aesthetic sensibilities, political values, and software engineering skills. You can learn more about me through the links and projects below.";
  let currentbio = "I'm";

  import { onMount } from 'svelte';

  let color =  "#FFFFF";

  onMount(() => {
    const changeColor = (event) => {
      const x = event.clientX;
      const y = event.clientY;
      color = `rgb(${x % 255}, ${y % 255}, ${(x + y) % 255})`;
    }
    
    window.addEventListener('mousemove', changeColor);
  });
</script>

<div class="content">
  <p transition:slide={{ duration: 400 }}>
    {shortbio}
    {#if expanded}
      <span>{extrabio}</span>
    {/if}
    <a on:click|preventDefault={toggleBio} style="color: green; cursor: pointer;">[{expanded ? 'less' : 'more'}]</a>
  </p>
  <p>{currentbio} 
    <span style="color: {color}; cursor: text;" >open to work!</span>
  </p>
</div>

<style>

</style>
