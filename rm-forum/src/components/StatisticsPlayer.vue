<script>
export default {
    props : {
        players : {
            type : Array,
            required : true,
        }
    },
    computed : {
        positionList () {
            const positions = ['CF', 'LWF', 'RWF', 'AMF', 'LMF', 'RMF', 'CMF', 'CD', 'LB', 'RB', 'GK']
            const statistics = {
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

            this.players.forEach(player => {
                positions.forEach(position => {
                    if (player.position.indexOf(position) > -1) {
                        statistics[position] += 1
                    }
                })
            })

            return statistics
        }
    },
}
</script>


<template>
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