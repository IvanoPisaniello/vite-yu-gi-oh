<script>
import axios from "axios";
export default {
    data() {
        return {
            archetypes: "",
            selectedArchetype: "",


        }
    },

    methods: {

        fetchArchetype() {
            const url = "https://db.ygoprodeck.com/api/v7/archetypes.php";

            axios.get(url).then((response) => {

                this.archetypes = response.data;

            })

        },


    },

    mounted() {
        this.fetchArchetype();
    }



}

</script>

<template>
    <select class="form-select" aria-label="Default select example" v-model="selectedArchetype">
        <option selected>Select Type</option>
        <option value="1" v-for="archetype in archetypes">
            {{ archetype.archetype_name }}
        </option>

    </select>
</template>


<style lang="scss" scoped>
select {
    width: 150px;
    margin-top: 50px;
}
</style>