<script>
import StatisticsPlayer from './components/StatisticsPlayer.vue';

export default {
    components : {
        StatisticsPlayer
    },
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
    methods: {
        addFavouritePlayer(player) {
            this.favouritePlayerList.push(player)
        },
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

    <!-- Add new players -->
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
    <!-- End add new players -->

    <hr>
    <!-- Statistic Players -->
    <StatisticsPlayer :players="playerList"/>
</template>