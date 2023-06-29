<script>
// @ts-nocheck

  import { onMount } from 'svelte';
  import { fade, slide } from 'svelte/transition';
  
  /**
     * @type {{ title: string; format: string; setting: string; date: string; info1: string; image: string; info2: string; }[]}
     */
  let projects = [];
  /**
     * @type {string | null}
     */
  let selectedCategory = null;
  let selectedProject = null;
  
  onMount(async () => {
    projects = (await import('../data/projects.json')).default;

    // group projects by format
    let groupedProjects = {};
    for (let project of projects) {
      if (!groupedProjects[project.format]) {
        groupedProjects[project.format] = [];
      }
      groupedProjects[project.format].push(project);
    }
    projects = groupedProjects;
  });

  function selectCategory(category) {
    selectedCategory = selectedCategory === category ? null : category;
  }

  function selectProject(project) {
    selectedProject = selectedProject === project ? null : project;
  }
</script>

{#each Object.keys(projects) as category (category)}
  <!-- svelte-ignore a11y-click-events-have-key-events -->
  <div class="category" on:click={() => selectCategory(category)}>
    {selectedCategory === category ? '[-]' : '[+]'} {category}
  </div>
  {#if selectedCategory === category}
    {#each projects[category] as project (project.title)}
      <!-- svelte-ignore a11y-click-events-have-key-events -->
      <div class="project-item" on:click={() => selectProject(project)}>
        <div class="project-content">
          <div class="project-text" class:selected={selectedProject === project}>
            <span class="title">- {project.title}</span>
            <span class="date">{project.date}</span>
          </div>
          {#if selectedProject === project}
            <div class="project-info">
              <p>{project.info1}</p>
              <div class="images">
                <!-- svelte-ignore a11y-missing-attribute -->
                <img src={project.image}/>
              </div>
              <p>{project.info2}</p>
              <a class="link" href={project.link.url}>{project.link.text}</a>          
            </div>
          {/if}
        </div>
      </div>
    {/each}
  {/if}
{/each}

<style>
.project-item {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;

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


.link{
  color: #FFFF;
  padding-bottom: 0.5rem;
}

.date {
  flex: 1;
  text-align: right;
}

.project-item:hover, .top-project:hover, .category:hover, .project-item:target {
  cursor: pointer;
}

.project-item:hover .title, .project-item:hover .date {
  text-decoration: underline;
}

.project-info {
  padding-top: 1rem;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  border-bottom: 0.5px dotted;
}

.images {
  display: flex;
}

.images img {
  max-width: 100%;
}

/* New style for selected project text */
.project-text.selected {
  text-decoration: underline;
  font-weight: bold;
}

/* add your own styles for the category div */
.category {
  /* styles here */
  padding: 0.5rem;
  cursor: pointer;
}
</style>
