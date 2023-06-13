<script>
    let projects = [
      { title: 'Project 1', format: 'Web App', date: 'June 2023' },
      { title: 'Project 2', format: 'Mobile App', date: 'May 2023' },
      { title: 'Project 3', format: 'Web App', date: 'April 2023' }
    ];
  </script>
  
  <div>
    {#each projects as project (project.title)}
      <div>
        <h2>{project.title}</h2>
        <p>{project.format} | {project.date}</p>
      </div>
    {/each}
  </div>
  