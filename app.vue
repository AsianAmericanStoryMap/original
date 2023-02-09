<template>

<div class="overflow-x-auto">
  <table class="table w-full">
    <!-- head -->
    <thead>
      <tr>
        <th>Date</th>
        <th>Status</th>
        <th>Place</th>
        <th>Description</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="(a,i) in 4" :key="i" class=" " :class="i==today ? 'active' : ''">
        <td>{{dates[i]}}</td>
        <td>
          <div v-if="isGame[i] && i >= today" class="badge badge-primary">GAME</div>
          <div v-else-if= "isGame[i]" class="badge badge-secondary">Past Game</div>
          <div v-else-if="i>=today" class="badge">Practice</div>
        </td>
        <td>{{ places[i] }}</td>
        <td>
          <div class="collapse">
            <input type="checkbox" /> 
            <div class="collapse-title text-xl font-medium">
              {{ collapseTitle[i] }}
            </div>
            <div class="collapse-content"> 
              <p>{{ description[i] }}</p>
            </div>
          </div>
        </td>
      </tr>
    </tbody>
  </table>
</div>
</template>

<script>

  export default{
    data(){
      return {
        dates : ["2/6","2/7","2/8","2/9"],
        isGame : [true,false,true,false],
        today : 2,
        places: ["Elkins", "PFAC", "Somewhere", "Overtherainbow"],
        collapseTitle:["A", "b","c","d"],
        description:["some longer description","I am doing this at 2 am","I need to read the Road","Maybe I will just watch youtube lol"]
      }
    }
  }
  

</script>


