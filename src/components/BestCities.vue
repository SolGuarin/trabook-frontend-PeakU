<template>
    <div class="card">
        <img v-bind:src="image" class="card-img-top img-fluid rounded img">
            <div class="card-body">
                <b-row>
                    <b-col class="City">
                        <p class="card-title">{{ city }}, {{ country }}</p>
                        <p class="trip-time"> {{ days_trip }} Days Trip</p>
                    </b-col>
                    <b-col class="price-score">
                        <p class="price">${{ price }}k</p>
                        <p class="score">⭐ {{ score }}</p>
                    </b-col>
                </b-row>
            </div>
    </div>
</template>

<script>
export default {
  name: 'BestCities',
  props:{
    image: String,
    city: String,
    country: String,
    days_trip: String,
    price: Number,
    score: Number
  }

}
</script>

<style scoped>
.card{
    border-radius: 5%;
}
.img{
    height: 18rem;
    width: 27rem;
    border: 0;
}
.card-title{
    font-size: 1.2rem;
    font-weight: bold;
    text-align: left;
}
.trip-time{
    font-size: 1.2rem;
    color: gray;
    text-align: left;
}
.price-score{
    display: flex;
    flex-direction: column;
    align-items: end;
}
.price{
    font-size: 1.2rem;
    color: darkorange;
    font-weight: bold; 
    text-align: center;
}
.score{
    font-size: 1.2rem;
    color: gray;
}
</style>