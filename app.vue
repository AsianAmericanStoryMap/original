<template>
  <div class="flex h-screen">

    <div class="btn-group btn-group-vertical">
      <button @click="gameSch = false" class="btn" :class="gameSch===false ? ' btn btn-active' : 'btn'">Week</button>
      <button @click="gameSch = true" class="btn" :class="gameSch === true ? 'btn-active' : 'btn'">Game</button>
    </div>

    `<div v-if="gameSch === false" class="overflow-x-auto">
      <table class="table">
        <thead>
          <tr>
            <th>Date</th>
            <th>Status</th>
            <th>Place</th>
            <th>Description</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(a, i) in dates" :key="i" class=" " :class="i == today ? 'active' : ''">
            <td>{{ dates[i]}}</td>
            <td>
              <div v-if="isGame.includes(i) && i >= today" class="badge badge-primary">GAME</div>
              <div v-else-if="isGame.includes(i)" class="badge badge-secondary">Past Game</div>
              <div v-else-if="i >= today" class="badge">Practice</div>
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

    <div v-else class="overflow-x-auto">
      <table class="table">
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
          <tr v-for="a in isGame" :key="a" class=" " :class="a == today ? 'active' : ''">
            <td>{{ dates[a]}}</td>
            <td>
              <div v-if="a >= today" class="badge badge-primary">GAME</div>
              <div v-else class="badge badge-secondary">Past Game</div>
            </td>
            <td>{{ places[a] }}</td>
            <td>
              <div class="collapse">
                <input type="checkbox" />
                <div class="collapse-title text-xl font-medium">
                  {{ collapseTitle[a] }}
                </div>
                <div class="collapse-content">
                  <p>{{ description[a] }}</p>
                </div>
              </div>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
export default {

  data() {
    return {
      dates: ["2/6", "2/7", "2/8", "2/9"],
      isGame: [0, 2],
      today: 2,
      places: ["Elkins", "PFAC", "Somewhere", "Overtherainbow"],
      collapseTitle: ["A", "b", "c", "d"],
      description: ["some longer description", "I am doing this at 2 am", "I need to read the Road", "Maybe I will just watch youtube lol"],
      gameSch: false,
    };
  },
};
</script>