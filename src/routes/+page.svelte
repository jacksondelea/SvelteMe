<script>
    import Bio from '../components/Bio.svelte';
    import Projects from '../components/Projects.svelte';
    import NameLogo from '../components/NameLogo.svelte';
    import Contact from '../components/Contact.svelte';
    import ThemeToggle from '../components/ThemeToggle.svelte';
    import BottomProjectBorder from '../components/BottomProjectBorder.svelte';
  </script>


<div class="content">
  <div class="infoindent">
    <div class="topbar">
      <NameLogo />
    </div>
    <div class="text">
      <Bio />
    </div>
    <Contact />
  </div>
  <Projects />
  <BottomProjectBorder />
</div>

<style>
    .topbar{
      display: flex;
      justify-content: space-between;
      align-items: center;
    }
    .infoindent{
      margin-left: 0.5rem;
      margin-right: 0.5rem;
    }
    .content {
      max-width: 420px;
      margin: 0 auto;
      margin-top: 20vh;
    }

    .text{
    max-width: 600px;
  }

  @media (max-width: 1024px) {  
    .content {
      margin-top: 2.5rem; 
    }
  }

  @media (max-width: 768px) {
    .content {
      width: 100%;
    }
  }

  @media (max-width: 480px) {
    .content {
      width: 95%;
    }
  }
</style>