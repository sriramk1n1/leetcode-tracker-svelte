<script>
    import { onMount } from "svelte";
    import Collapse from "./collapse.svelte";
    let dark=false;
    let data;
    let set=false;
    fetch("http://3.110.130.68:8000/api/weekly").then(response=>response.json()).then(obj=>{data=obj;set=true;});

</script>

<nav class="navbar navbar-expand-lg" class:bg-secondary-subtle={!dark} class:bg-dark={dark} class:text={dark}>
    <div class="container-fluid">
      <span class="navbar-brand">Navbar</span>
      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul class="navbar-nav me-auto mb-2 mb-lg-0">
          <li class="nav-item">
            <a class="nav-link active" aria-current="page" href="/weekly">Weekly</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="/progress">Progress</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="/leaderboard">Leaderboard</a>
          </li>
        </ul>
        <button on:click={()=>{window.document.body.classList.toggle('dark-mode');dark=!dark;console.log(obj)}} class="dmode">
            <img src="dark-mode.png" height="25px" width="25px" alt="mode" class="d-flex" />
            </button>
      </div>
    </div>
  </nav>


{#key data}
{#if set}
{#each Object.entries(data) as [i,j],index}
  <Collapse id={i} obj={j} index={index+1}></Collapse>
{/each}
{:else}
<div> Waiting...</div>
{/if}
{/key}

















<style>

    .dmode{
        background: none;
        color: inherit;
        border: none;
        padding: 0;
        font: inherit;
        cursor: pointer;
        outline: inherit;
    }
    :global(body.dark-mode){
        background-color: #1c1c1c;
        color: white;
    }
</style>