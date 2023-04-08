<template>
    <div class="card">
        <img v-bind:src="img" class="card-img-top img-fluid rounded img">
            <div class="card-body">
              <p class="card-title">{{ title }}</p>
              <p class="card-text">{{ date }}</p>
            </div>
    </div>
</template>

<script>
export default {
  name: 'BlogPost',
  props: {
    img: String,
    title: String,
    date: Date
  }
}
</script>

<style scoped> 
.card{
    border: 0;
    background-color: #fffbf3;
}
.img{
    height: 18rem;
    width: 25rem;
    border: 0;
}
.card-title{
    font-size: 1.3rem;
    line-height: normal;
}
.card-text{
    font-size: 1.2rem;
    color: gray;
}
.card-body{
    text-align: left;
}
</style>