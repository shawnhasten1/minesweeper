<template>
    <div class="tile" :style="{color:color, backgroundColor:backgroundColor}" @click="$emit('reveal')" @click.right.prevent="$emit('flag')">{{ content }}</div>
</template>

<script>
export default{
    props:{
        tile: Object
    },
    computed: {
        content(){
            if(this.tile.flagged) return "❌";
            if(!this.tile.revealed) return "";
            if(this.tile.bomb) return "💣";
            if(this.tile.surroundingBombs) return this.tile.surroundingBombs;
            return "";
        },
        color(){
            if(this.tile.surroundingBombs == 1) return "blue";
            if(this.tile.surroundingBombs == 2) return "green";
            if(this.tile.surroundingBombs == 3) return "red";
            if(this.tile.surroundingBombs == 4) return "purple";
            if(this.tile.surroundingBombs == 5) return "brown";
            if(this.tile.surroundingBombs == 6) return "turquoise";
            if(this.tile.surroundingBombs == 7) return "black";
            return "grey";
        },
        backgroundColor(){
            if(this.tile.revealed) return "#eee"; 
            return "";
        }
    },
    methods:{
    }
}
</script>


<style scoped>
.tile {
    width: 50px;
    height: 50px;
    border: 1px solid lightgray;
    display: flex;
    align-items: center;
    justify-content: center;
}
</style>