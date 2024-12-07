<script>
export default {
  data : () => ({
    playerList : [
      {
          name : 'Ronaldo',
          position : ['CF', 'LWF', 'LMF', 'RWF', 'RMF']
      },
      {
          name : 'Vini Junior',
          position : ['CF', 'LWF', 'LMF']
      },
      {
          name : 'Mbappe',
          position : ['CF', 'LWF', 'LMF', 'RWF', 'RMF']
      },
      {
          name : 'Kaka',
          position : ['LMF', 'RMF', 'AMF', 'CMF']
      },
      {
          name : 'Ramos',
          position : ['CD']
      }],
    favouritePlayerList : [],
    newPlayer : {name : '', position : []},
  }),
  computed: {
    CFList () {
      return this.playerList.filter(
          player => player.position.indexOf('CF') > -1
      )
    },
    positionList () {
      const positions = ['CF', 'LWF', 'RWF', 'AMF', 'LMF', 'RMF', 'CMF', 'CD', 'LB', 'RB', 'GK']
      const statistics = {cas
          CF: 0,
          LWF: 0,
          RWF: 0,
          LMF: 0,
          AMF: 0,
          RMF: 0,
          CMF: 0,
          CD: 0,
          RB: 0,
          LB: 0,
          GK: 0,
      }

      this.playerList.forEach(player => {
          positions.forEach(position => {
              if (player.position.indexOf(position) > -1) {
                  statistics[position] += 1
              }
          })
      })

      return statistics
    }
  },
  methods: {
    addFavouritePlayer(player) {
        this.favouritePlayerList.push(player)
    },
    // addNewPlayer() {
    //     this.playerList.push(this.newPlayer)
    //     this.newPlayer = {name: '', position : []}
    // }
    addNewPlayer() {
        // Validate that both name and at least one position are provided
        if (this.newPlayer.name && this.newPlayer.position.length > 0) {
            this.playerList.push({ ...this.newPlayer }); // Push a copy of the player
            this.newPlayer = { name: '', position: [] }; // Reset the form
        } else {
          console.log('No player added')
        }
    }
  }
}
</script>

<template>
  <h1>Real Madrid Players</h1>
        <p v-if="playerList.length === 0">No players in Real Madrid</p>
        <ul v-else>
            <li v-for="player in playerList">
                <button @click="addFavouritePlayer(player)">⭐️{{ player.name }}</button>
            </li>
        </ul>
        <hr>
        <h1>Real Madrid Favourite Players</h1>
        <ul v-if="favouritePlayerList.length > 0">
            <li v-for="favouritePlayer in favouritePlayerList">{{ favouritePlayer.name }}</li>
        </ul>
        <p v-else>No favourite player in Real Madrid</p>
        <h2>Add new player</h2>
        <!-- Input for player's name -->
        <input
            type="text"
            v-model="newPlayer.name"
            placeholder="Player Name"
        >

        <!-- Multiselect dropdown for positions -->
        <select v-model="newPlayer.position" multiple>
            <option value="CF">CF</option>
            <option value="LWF">LWF</option>
            <option value="RWF">RWF</option>
            <option value="AMF">AMF</option>
            <option value="LMF">LMF</option>
            <option value="RMF">RMF</option>
            <option value="CMF">CMF</option>
            <option value="CD">CD</option>
            <option value="LB">LB</option>
            <option value="RB">RB</option>
            <option value="GK">GK</option>
        </select>

        <!-- Add player button -->
        <button @click="addNewPlayer">Add Player</button>
        <hr>
        <h1>Statistic in Real Madrid Players</h1>
        <ul>
            <!-- <li>CF: {{ CFList.length }}</li>
            <li>LWF: </li>
            <li>RWF: </li>
            <li>AMF: </li>
            <li>LMF: </li>
            <li>RMF: </li>
            <li>CMF: </li>
            <li>CD: </li> -->
            <li v-for="(stat, position) in positionList">
                {{ position }} : {{ stat }}
            </li>
        </ul>
</template>