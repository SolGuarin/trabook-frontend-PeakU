<template>
    <div class="card">
        <img v-bind:src="img" class="card-img-top img-fluid rounded img">
            <div class="card-body">
                <b-row>
                    <b-col>
                      <p class="card-title">{{ city }}</p>
                      <p class="card-text">{{ country }}</p>
                    </b-col>
                    <b-col class="container-price">
                      <p class="price">{{ price }}</p>
                    </b-col>
                    <b-col class="container-discount">
                      <p class="score">⭐{{ score }}</p>
                      <p class="discount">{{ discount }}</p>
                    </b-col>
                </b-row>
            </div>
    </div>
</template>

<script>
export default {
  name: 'DealsAndDiscounts',
  props: {
    img: String,
    city: String,
    country: String,
    score: String,
    price: Number,
    discount: Number
  }
}
</script>

<style scoped>
.card{
    border-radius: 5%;
}
.img{
    border: 0;
    height: 18rem;
}
.card-title{
    font-size: 1.4rem;
    font-weight: bold;
}
.card-text{
    font-size: 1.2rem;
    color: gray;
    text-align: left;
}
.container-price{
    display: flex;
    align-items: flex-end;
    justify-content: end;
    margin-left: 0;
}
.price{
    font-size: 1rem;
    color: gray;
    text-decoration: line-through;
}
.container-discount{
    padding-top: 1rem;
    display: flex;
    flex-direction: column;
    align-items: end;
    
}
.score{
    font-size: 0.9rem;
    color: gray;
}
.discount{
    width: 2rem;
    font-size: 1rem;
    border-radius: 0.5rem;
    color: darkorange;
    background-color:#f5d6a0;
    font-weight: bold; 
}
</style>
