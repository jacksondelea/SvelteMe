<script>
  let projects = [
    { title: 'Project 1', format: 'Web App', date: 'June 2023', info1: 'Project 1 info...', info2: 'Project 1 info 2' },
    { title: 'Project 2', format: 'Mobile App', date: 'May 2023', info1: 'Project 2 info...', info2: 'Project 2 info 2' },
    { title: 'Project 3', format: 'Web App', date: 'April 2023', info1: 'Project 3 info...', info2: 'Project 3 info 2' }
  ];
  let selectedProject = null;
  
  function selectProject(project) {
    selectedProject = selectedProject === project ? null : project;
  }
</script>

{#each projects as project (project.title)}
  <!-- svelte-ignore a11y-click-events-have-key-events -->
  <div class="project-item" on:click={() => selectProject(project)}>
    <div class="project-content">
      <div class="project-text">
        <span class="title">{project.title}</span>
        <span class="format">{project.format}</span>
        <span class="date">{project.date}</span>
      </div>
      {#if selectedProject === project}
        <div class="project-info">
          <p>{project.info1}</p>
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

</style>
