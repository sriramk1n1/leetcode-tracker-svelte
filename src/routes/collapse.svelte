<script>
    export let id = "id";
    export let index;
    export let obj;
</script>

<div class="card">
<p class="d-inline-flex gap-1">
    <button class="btn btn-primary d-flex" type="button" data-bs-toggle="collapse" data-bs-target="#collapseExample{id}" aria-expanded="false" aria-controls="collapseExample">
      Week - {index} 
    </button>
  </p>
  <div class="collapse" id="collapseExample{id}">
    <div class="card-body">
      <div> Topic: {obj.topic}</div>
      <ul>
        <li>Q1 : <a href={obj.q1}>{obj.q1}</a></li>
        <li>Q2 : <a href={obj.q2}>{obj.q2}</a></li>
        <li>Q3 : <a href={obj.q3}>{obj.q3}</a></li>
        <li>Q4 : <a href={obj.q4}>{obj.q4}</a></li>
        <li>Q5 : <a href={obj.q5}>{obj.q5}</a></li>

      </ul>
    </div>
  </div>
</div>




<style>

</style>