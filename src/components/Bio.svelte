<script>
  let expanded = false;
  function toggleBio() {
    expanded = !expanded;
  }

  let shortbio = 'Researcher, writer and designer based in New York City.';
  let longbio1= "Researcher, writer and designer based in New York City. I got my B.A. from Brown University, where I studied a mix of literature, computer science, architecture, theory, and design. I'm interested in critical engineering, information architecture, AI, and algorithmic culture.";
  let longnio2 = "Previously at elsewhere and Interscope."
  let currentbio = "I'm currently a researcher and artist for Forensic Architecture."

  
  function changeColor(event) {
    const x = event.clientX;
    const y = event.clientY;
    const color = `rgb(${x % 255}, ${y % 255}, ${(x + y) % 255})`;
    event.target.style.color = color;
  }

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
  <p>{expanded ? longbio1 : shortbio} <a on:click|preventDefault={toggleBio} style="color: green; cursor: pointer;">[{expanded ? 'less' : 'more'}]</a></p>
  <p>{currentbio} I'm 
    <span style="color: {color}; cursor: text;" >open to work!</span>
  </p>
</div>

<style>

</style>
