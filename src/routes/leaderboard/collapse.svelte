<script>
    import {dark} from "$lib/store.js";
    export let obj;
</script>

<div class="card" style="width: 100%" class:bg-dark={$dark} class:text-white={$dark}>
    <div class="card-body">
        <ul>
            <!-- <li class="list">Name: {obj.name}</li> -->
            <li class="list">User name: {obj.user_name}</li>
            <li class="list">Total Solved: {obj.total}</li>
            <li class="list">This week: {obj.week}</li>
            <li class="list">Today: {obj.today}</li>
        </ul>
    </div>
  </div>



<style>
.list{
    display:inline-block;
    padding-right:10px;
}
</style>