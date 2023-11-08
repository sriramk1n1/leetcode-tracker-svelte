<script>
    import Collapse from "./collapse.svelte";
    import {dark} from "$lib/store.js";
    import img from "$lib/dark-mode.png"
    import {  onMount } from "svelte";
    let data;
    let set=false;

    onMount(()=>{
      if (localStorage.dark==="true"){
        $dark=true;
        window.document.body.classList.add('dark-mode')
      }
      fetch("https://gdsc.skapi.online/api/weekly").then(response=>response.json()).then(obj=>{data=obj;set=true;});
    })
</script>

<nav class="navbar navbar-expand-lg" class:bg-secondary-subtle={!$dark} class:navbar-dark={$dark} class:bg-dark={$dark}>
    <div class="container-fluid dark-mode">
        <ul class="navbar-nav me-auto mb-2 mb-lg-0">
          <li class="nav-item">
            <a class="nav-link active" aria-current="page" href="/">Questions</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="/leaderboard">Leaderboard - Leetcode</a>
          </li>
        </ul>
        <button on:click={()=>{
        $dark=!$dark;
        if ($dark==true){
          window.document.body.classList.add('dark-mode')
        }else{
          window.document.body.classList.remove('dark-mode')
        }
        window.localStorage.dark=$dark?"true":"false";
        }} class="dmode">
            <img src={img} height="25px" width="25px" alt="mode" class="d-flex" />
            </button>
      </div>
  </nav>


{#if set}
{#each Object.entries(data) as [i,j],index}
  <Collapse id={i} obj={j} index={index+1}></Collapse>
{/each}
{:else}
<!-- svelte-ignore a11y-missing-attribute -->
<div class="loading"><iframe src="https://giphy.com/embed/3oEjI6SIIHBdRxXI40" width="30%" height="50%"></iframe></div>
{/if}

















<style>
  :global(body){
    box-sizing: border-box;
  }
  .loading{
    text-align: center;
  }
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
