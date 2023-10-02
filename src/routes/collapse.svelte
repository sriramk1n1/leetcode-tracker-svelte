<script>
    import {dark} from "$lib/store.js";
    export let id;
    export let index;
    export let obj;
    $: console.log(obj)
</script>

<div class="card container-fluid" data-bs-toggle="collapse" data-bs-target="#collapseExample{id}" class:bg-dark={$dark} class:text-white={$dark}>
<p class="d-inline-flex gap-1">
    <span style="padding-top: 15px"> Week - {index}  </span>
    <button class="dmode" style="padding-top: 15px" type="button" data-bs-toggle="collapse" data-bs-target="#collapseExample{id}" aria-expanded="false" aria-controls="collapseExample">
      +
    </button>
  </p>
  <div class="collapse" id="collapseExample{id}">
    <div class="card-body">
      <div> Topic: {obj.topic}</div>
      <ul>
        {#if obj.d1}
        <li>{obj.d1} -- Q1 : <a href={obj.q1}>{obj.q1}</a></li>
        {/if}
        {#if obj.d2}
        <li>{obj.d2} -- Q@ : <a href={obj.q2}>{obj.q2}</a></li>
        {/if}
        {#if obj.d3}
        <li>{obj.d3} -- Q1 : <a href={obj.q3}>{obj.q3}</a></li>
        {/if}
        {#if obj.d4}
        <li>{obj.d4} -- Q1 : <a href={obj.q4}>{obj.q4}</a></li>
        {/if}
        {#if obj.d5}
        <li>{obj.d5} -- Q1 : <a href={obj.q5}>{obj.q5}</a></li>
        {/if}
      </ul>
    </div>
    <div class="card-body">
      {#if obj.r1}
          References:
      {/if}
      <ul>
        
        {#if obj.r1}
        <li><a href={obj.r1}>{obj.r1}</a></li>
        {/if}
        {#if obj.r2}
      <li><a href={obj.r2}>{obj.r2}</a></li>
      {/if}
      {#if obj.r3}
      <li><a href={obj.r3}>{obj.r3}</a></li>
      {/if}
      {#if obj.r4}
      <li><a href={obj.r4}>{obj.r4}</a></li>
      {/if}
      {#if obj.r5}
      <li><a href={obj.r5}>{obj.r5}</a></li>
      {/if}
    </ul>
  </div>
  </div>
</div>




<style>
.dmode{
        margin-left: 10px;
        padding-left: 10px;
        background: none;
        color: inherit;
        border: none;
        padding: 0;
        font: inherit;
        cursor: pointer;
        outline: inherit;
    }
</style>