<template>
        <div class="card">
            <img v-bind:src="img" class="card-img-top img-fluid img-thumbnail rounded img">
                <div class="card-body">
                    <p class="card-title">{{ title }}</p>
                    <p class="card-text"> {{ text }}</p>         
                </div>
        </div>
</template>

<script>
export default {
  name: 'FirstCard',
  props: {
    img: String,
    title: String,
    text: String
  }
}

</script>

<style scoped>
.container-card{
    height: 20rem;
    width: 20rem;
}
.card{
    border-radius: 5%;
}
.img{
    height: 5rem;
    width: 5rem;
    border: 0;
    margin-left: 0.5rem;
}
.card-title{
    font-size: 1.8rem;
    font-weight: bold;
}
.card-text{
    font-size: 1.2rem;
    color: gray;

}

</style>