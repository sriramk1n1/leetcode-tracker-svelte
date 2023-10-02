<script>
    import Collapse from "./collapse.svelte";
    import {dark} from "$lib/store.js";
    import img from "$lib/dark-mode.png"
    import { onMount } from "svelte";
    
    let data;
    let set=false;
    onMount(()=>{
      if (localStorage.dark==="true"){
        $dark=true;
        window.document.body.classList.add('dark-mode')
      }
      fetch("https://skapi.online/api/leaderboard-today").then(response=>response.json()).then(obj=>{data=obj;set=true;});
    })
/* When the user clicks on the button,
toggle between hiding and showing the dropdown content */
function myFunction() {
  document.getElementById("myDropdown").classList.toggle("show");
}

// Close the dropdown menu if the user clicks outside of it
window.onclick = function(event) {
  if (!event.target.matches('.dropbtn')) {
    var dropdowns = document.getElementsByClassName("dropdown-content");
    var i;
    for (i = 0; i < dropdowns.length; i++) {
      var openDropdown = dropdowns[i];
      if (openDropdown.classList.contains('show')) {
        openDropdown.classList.remove('show');
      }
    }
  }
}
</script>

<nav class="navbar navbar-expand-lg" class:bg-secondary-subtle={!$dark} class:navbar-dark={$dark} class:bg-dark={$dark}>
    <div class="container-fluid">
        <ul class="navbar-nav me-auto mb-2 mb-lg-0">
          <li class="nav-item">
            <a class="nav-link" aria-current="page" href="/">Questions</a>
          </li>
          <li class="nav-item">
            <a class="nav-link active" href="/leaderboard">Leaderboard</a>
          </li>
          <li class="nav-item">
            <div class="dropdown">
              <button on:click={myFunction} class="dropbtn nav-link"> Sort By</button>
              <div id="myDropdown" class="dropdown-content">
                <a href="/leaderboard">Total Solved</a>
                <a href="/leaderboard/today">Solved Today </a>
                <a href="/leaderboard/week">Solved this week </a>
              </div>
            </div>
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


{#key data}
{#if set}
{#each Object.entries(data) as [i,j],index}
  <Collapse obj={j}></Collapse>
{/each}
{:else}
<!-- svelte-ignore a11y-missing-attribute -->
<div class="loading"><iframe src="https://giphy.com/embed/3oEjI6SIIHBdRxXI40" width="30%" height="50%"></iframe></div>
{/if}
{/key}












<div class="show"></div>




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
    .dropbtn {
  background-color: transparent;
  border: none;
  cursor: pointer;
}

/* Dropdown button on hover & focus */
.dropbtn:hover, .dropbtn:focus {
  background-color: none;
}

/* The container <div> - needed to position the dropdown content */
.dropdown {
  position: relative;
  display: inline-block;
}

/* Dropdown Content (Hidden by Default) */
.dropdown-content {
  display: none;
  position: absolute;
  background-color: #f1f1f1;
  min-width: 160px;
  box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.2);
  z-index: 1;
}

/* Links inside the dropdown */
.dropdown-content a {
  color: black;
  padding: 12px 16px;
  text-decoration: none;
  display: block;
}

/* Change color of dropdown links on hover */
.dropdown-content a:hover {background-color: #ddd;}

/* Show the dropdown menu (use JS to add this class to the .dropdown-content container when the user clicks on the dropdown button) */
.show {display:block;}
</style>
