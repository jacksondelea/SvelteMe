<script>
  import { slide } from 'svelte/transition';

  let expanded = false;
  function toggleBio() {
    expanded = !expanded;
  }

  let shortbio = 'Technologist, writer and designer based in New York City.';
  let extrabio= "I got my B.A. from Brown University, where I studied a mix of literature, computer science, architecture, theory, and design. I'm interested in how technology, politics and culture interact to produce new social conditions. Right now, I'm particularly interested in distributed networks, open source software, and durable interface design. I'm working on developing a critical design practice that connects my aesthetic sensibilities with my political values and software engineering skills. You can learn more about me through the links and projects below.";
  let currentbio = "I'm";

  import { onMount } from 'svelte';

  let color =  "#FFFFF";
  let isBlack = false;

  onMount(() => {
    const changeColor = (event) => {
      const x = event.clientX;
      const y = event.clientY;
      if (!isBlack) {
        color = `rgb(${x % 255}, ${y % 255}, ${(x + y) % 255})`;
      }
    }
    
    window.addEventListener('mousemove', changeColor);
  });

  function toggleWorkColor() {
    isBlack = !isBlack;
    if (isBlack) {
      color = "#FFFF";
    }
  }
</script>

<div class="content">
  <p transition:slide={{ duration: 400 }}>
    {shortbio}
    {#if expanded}
      <span>{extrabio}</span>
    {/if}
    <a on:click|preventDefault={toggleBio} style="color: #0a58d0; cursor: pointer;">[{expanded ? 'less' : 'more'}]</a>
  </p>
  <p>{currentbio} 
    <span style="color: {color}; cursor: pointer;" on:click={toggleWorkColor}>open to work!</span>
  </p>
</div>

<style>
.content{
  border-top: 0.5px solid #121212;
}
</style>
