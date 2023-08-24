<script>
import axios from "axios";
import Card from "./Card.vue"
export default {
    Card,

    data() {
        return {
            cards: [],

        }
    },
    methods: {

        fetchCards() {
            const url = "https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0"

            axios.get(url).then((response) => {


                this.cards = response.data.data;
                console.log(this.cards)
            })



        }
    },
    mounted() {
        this.fetchCards();

    }


}


</script>


<template>
    <div class="container">
        <div class="row">
            <div class="card-counter">
                <p class="text-white p-2">Found 20 cards</p>
            </div>

            <div class="col" v-for="card in cards" :key="card.id">

                <div class="card text-start mb-3">
                    <img class="card-img-top" :src="card.card_images[0].image_url" alt="Title">
                    <div class="card-body">
                        <h4 class="card-title">{{ card.name }}</h4>
                        <p class="card-text">{{ card.archetype }}</p>
                    </div>
                </div>

            </div>
        </div>
    </div>
</template>

<style lang="scss" scoped>
.card-counter {
    height: 50px;
    background-color: black;
}

.container {
    width: 900px;

}

img {
    height: 200px;


}

.card {
    background-color: orange;
    height: 300px;
    min-width: 150px;

    h4 {
        font-size: 1rem;
        text-align: center;
        color: white;
    }

    p {
        font-size: .8rem;
        text-align: center;
    }
}
</style>