<script>
  import { onMount } from 'svelte';
  import { fade, slide } from 'svelte/transition';
  
  /**
     * @type {any[]}
     */
  let projects = [];
  /**
     * @type {null}
     */
  let selectedProject = null;
  
  onMount(async () => {
    // dynamically import your JSON file
    projects = (await import('../data/projects.json')).default;
  });

  /**
     * @param {null} project
     */
  function selectProject(project) {
    selectedProject = selectedProject === project ? null : project;
  }
</script>

{#each projects as project (project.title)}
  <!-- svelte-ignore a11y-click-events-have-key-events -->
  <div class="project-item" on:click={() => selectProject(project)} transition:fade={{ duration: 100 }}>
    <div class="project-content">
      <div class="project-text" class:selected={selectedProject === project}>
        <span class="title">{project.title}</span>
        <span class="format">{project.format}</span>
        <span class="setting">{project.setting}</span>
        <span class="date">{project.date}</span>
      </div>
      {#if selectedProject === project}
        <div class="project-info" transition:slide={{ duration: 100 }}>
          <p>{project.info1}</p>
          <div class="images">
            <img src={project.image}/>
          </div>
          <p>{project.info2}</p>          
        </div>
      {/if}
    </div>
  </div>
{/each}

<style>
.project-item {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  border-top: 0.5px solid;
  padding: 0.5rem;
}

.project-content {
  display: flex;
  flex-direction: column;
  width: 100%;
}

.project-text {
  display: flex;
  justify-content: space-between;
}

.title {
  flex: 2;
}

.format {
  flex: 1;
  text-align: left;
}

.setting {
  flex: 1;
  text-align: center;
}

.date {
  flex: 1;
  text-align: right;
}

.project-item:hover, .top-project:hover, .project-item:target {
  transition: background 0.5s ease;
  background: darkgreen;
  color: #FFFF;
  cursor: pointer;
}

.project-info {
  padding-top: 1rem;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
}

.images {
  display: flex;
}

/* New style for selected project text */
.project-text.selected {
  text-decoration: underline;
  font-weight: bold;
}

</style>
