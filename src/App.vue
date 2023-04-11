<template>
  <div id="app">
  <!--PAGINA1-->
  <b-container class="container-1">
    <b-row class="header">
      <b-col cols="2" class="row-1">
        <img class="logo" src="./assets/Logotipo.png" alt="">
      </b-col>

      <b-col class="row-2">
        <b-nav >
          <b-nav-item class="text-dark" v-for=" (item, i) in itemsNav" :key="'A' + i" active>
             {{ item }}
          </b-nav-item>
        </b-nav>
      </b-col>

      <b-col cols="4" class="row-3">
          <p class="login">{{ login }}</p>
          <button class="button-signup">{{ signup }}</button>
      </b-col>
    </b-row>
    
    <b-row class="fila-2">
      <b-col class="colum-1">
        <p class="titulo-1"> {{ titulo1 }}</p>
        <p class="parrafo-1"> {{ parrafo1 }}</p>
        <button class="buttondiscover"> {{ buttondiscover }}</button>
      </b-col>
        
      <b-col class="colum-2">
        <img class="imgtourist" src="./assets/tourist.png">  
      </b-col>
    </b-row>

    <b-row class="fila-3">
      <b-row class="form">
        <b-col>
          <div>
            <b-dropdown id="dropdown-1" text="Location" variant="white" class="m-md-2">
                <b-dropdown-item>First Action</b-dropdown-item>
                <b-dropdown-item>Second Action</b-dropdown-item>
                <b-dropdown-item>Third Action</b-dropdown-item>
            </b-dropdown>
          </div>
          <p>Where are you going</p>
        </b-col>

        <b-col>
          <div>
            <b-dropdown id="dropdown-2" text="Date" variant="white" class="m-md-2">
                <b-dropdown-item>First Action</b-dropdown-item>
                <b-dropdown-item>Second Action</b-dropdown-item>
                <b-dropdown-item>Third Action</b-dropdown-item>
            </b-dropdown>
          </div>
          <p>When you will go</p>
        </b-col>

        <b-col>
          <div>
            <b-dropdown id="dropdown-3" text="Guest" variant="white" class="m-md-2">
                <b-dropdown-item>First Action</b-dropdown-item>
                <b-dropdown-item>Second Action</b-dropdown-item>
                <b-dropdown-item>Third Action</b-dropdown-item>
            </b-dropdown>
          </div>
          <p>Number of guest</p>
        </b-col>

        <b-col>
          <button class="buttonexplore">Explore Now</button>
        </b-col>

      </b-row>
    </b-row>
  </b-container>

  <!--PAGINA2-->
  <b-container class="container-2">
    <b-row class="pag2-row1">
        <p class="title-pag2">Things you need to do</p>
        <p class="subtitle-pag2">We ensure that you'll embark on a perfectly planned, safe vacation at a price you can afford. </p>
    </b-row>

    <b-row class="pag2-row2">
      <div class="container-cards-pag2" >
        <div class="style-card" v-for= "(item, i) in contentCard" :key="'B' + i">
          <FirstCard :img="item.img" :title="item.title" :text="item.text"/>
        </div>
      </div>
    </b-row>
  </b-container>
  
  <!--PAGINA3-->
  <b-container class="container-3">
      <b-row class="pag3-row1">
          <p class="title-pag3">Exclusive deals & discounts </p>
          <p class="subtitle-pag3">Discover our fantastic early booking discounts & start planning your journey.</p>
      </b-row>

      <b-row class="pag3-row2">
        <b-col class="container-card-pag3" v-for= "(item, i) in triplistdiscount" :key="'C' + i">
          <DealsAndDiscounts :image="item.image" :city="item.city" :country="item.country" :score="item.score" :price="item.price" :promo_price="item.promo_price"/>
        </b-col>
      </b-row>

      <b-row class="pag3-row3">
        <b-pagination v-model="currentPage" pills :total-rows="rows" size="sm"></b-pagination>
      </b-row>
  </b-container>

  <!--PAGINA4-->
  <b-container class="container-4">
    <b-row class="pag4-row1">
      <p class="title-pag4">Best vacation plan </p>
      <p class="subtitle-pag4">Plan your perfect vacation with our travel agency. Choose amoung hundreds of all-inclusive offers!</p>
    </b-row>

    <b-row class="pag4-row2">
        <b-pagination v-model="currentPage" pills :total-rows="rows" size="sm"></b-pagination>
    </b-row>

    <b-row class="pag4-row3">
      <b-col class="container-card-pag3" v-for="(item, i) in bestTrips" :key="'D' + i">
        <BestCities :image="item.image" :city="item.city" :country="item.country" :days_trip="item.days_trip" :price="item.price" :score="item.score"/>
      </b-col>
    </b-row>
  </b-container>

  <!--PAGINA5-->
  <b-container class="container-5">
      <b-row class="pag5-row1">
          <b-col cols="5" class="pag5-row1-col1">
              <p class="title-pag5">What people say about us.</p>
              <p class="subtitle-pag5">Our Clients send us bunch of smilies with our services and we love them.</p>
              <b-pagination v-model="currentPage" pills :total-rows="rows" size="sm"></b-pagination>
          </b-col>

          <b-col cols="7" class="row1-col2 container-review">
            <div class="review" v-for="(item ,i) in review" :key="'E' + i">

                  <img class="img-reviewer" v-bind:src="item.image" alt="">

              <div class="review-content" v-for="(item ,i) in review" :key="'F' + i">
                  {{ item.text }}
              </div>

              <div class="name" v-for="(item ,i) in review" :key="'G' + i">
                {{ item.reviewer }}
                <br>
                {{ item.city }},
                {{ item.country }}
              </div>

            </div>
          </b-col>
      </b-row>
  </b-container>

  <!--PAGINA6-->
  <b-container class="container-6">
    <b-row class="pag6-row1">
      <p class="title-pag6">Get update with latest blog</p>
    </b-row>
      
    <b-row class="pag6-row2">
      <b-col class="container-card-pag6" v-for= "(item, i) in blogpost" :key="'H' + i">
        <BlogPost :image="item.image" :title="item.title" :date="item.date"/>
      </b-col>
    </b-row>
  </b-container>

    <!--PAGINA7-->
  <b-container class="container-7">
    <b-row class="pag7-row1">
        <p class="title-pag7">Subscribe and get exclusive deals & offer</p>
        <div class="form-group">
          <img class="img-email" src="https://png.pngtree.com/png-vector/20190927/ourmid/pngtree-email-icon-png-image_1757854.jpg">
          <input type="email" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp" placeholder="Enter your email" style="border: 0;" >
          <button class="button-suscribe" >Subscribe</button>
          </div>
    </b-row>

    <b-row class="pag7-row2">
      <b-col class="pag7-row2-col1" cols="4">
        <img class="logo" src="./assets/Logotipo.png" alt="">
        <p class="subtitle-pag7" >Book your trip in minute, get full Control for much longer.</p>
        <div class="container-img-socialnetworks">
          <img class="img-socialnetwork" src="https://icones.pro/wp-content/uploads/2021/02/facebook-icone-orange.png" alt="">
          <img class="img-socialnetwork" src="https://icones.pro/wp-content/uploads/2021/02/instagram-icone-orange.png" alt="">
          <img class="img-socialnetwork" src="https://e1b775cfad.clvaw-cdnwnd.com/25b28317decbea527e48a93310c89d7d/200000200-751d1751d4/whatsapp%20%281%29.png?ph=e1b775cfad" alt="">
        </div>
      </b-col>

      <b-col class="pag7-row2-col2">
        <ul class="company">
          <li>Company</li>
        </ul>
        <ul class="company-items">
          <li v-for="(item, i) in companyitems" :key="'I' + i">
            {{ item }}
          </li>
        </ul>
      </b-col>

      <b-col class="pag7-row2-col3">
        <ul class="contact">
          <li>Contact</li>
        </ul>
        <ul class="contact-items">
          <li v-for="(item, i) in contactitems" :key="'J' + i">
            {{ item }}
          </li>
        </ul>
      </b-col>

      <b-col class="pag7-row2-col4">
        <ul class="more">
          <li>More</li>
        </ul>
        <ul class="more-items">
          <li v-for="(item, i) in moreitems" :key="'K' + i">
            {{ item }}
          </li>
        </ul>
      </b-col>
    </b-row>

    <b-row class="pag7-row3">
      <b-col class="pag7-row3-col1">
        <p class="copyrigth">Copyrigth, Trabook 2022. All rights reserved.</p>
      </b-col>
      <b-col class="pag7-row3-col2">
        <p class="condition">Terms & Conditions</p>
      </b-col>
    </b-row>
  </b-container>
  
  </div>
</template>

<script>
import axios from 'axios'
import FirstCard from './components/FirstCard.vue'
import DealsAndDiscounts from './components/DealsAndDiscounts.vue'
import BestCities from './components/BestCities.vue'
import BlogPost from './components/BlogPost.vue'

axios.defaults.headers.common['Access-Control-Allow-Origin'] = '*';

export default {
  name: 'App',
  components: {
    FirstCard,
    DealsAndDiscounts,
    BestCities,
    BlogPost
  },
  data() {
    return {
      itemsNav: ["Home", "About", "Destination", "Tour", "Blog"],
      login: "Login",
      signup: "Sign Up",
      titulo1: "Get started your exciting journey with us.",
      parrafo1: "A team of experienced tourism professionals will provide you with the best advice and tips for your desire place.",
      buttondiscover: "Discover Now",
      imgtourist: "./assets/tourist.png",
      contentCard: [{
        img: require('@/assets/Group2.png'),
        title: 'Sign Up',
        text: 'Completes all the work associated with planning and processing.'
      },{
        img: require('@/assets/Group.png'),
        title: 'Worth of Money',
        text: 'After successful access then book from exclusive deals & pricing.'
      },{
        img: require('@/assets/Group1.png'),
        title: 'Exciting Travel',
        text: 'Start and explore a wide and extensive range of exciting travel experience.'
      }],

      triplistdiscount: [

      ],
      rows: 100,
      currentPage:1,
      bestTrips: [
 
      ],
      review:[

      ],
  
      blogpost:[

      ],
      companyitems: ["About", "Careers", "Logistic", "Privacy & Policy"],
      contactitems: ["Help/FAQ", "Press", "Affilates"],
      moreitems: ["Press Centre", "Our Blog", "Low fare tips"]
  
    }
  },
  methods: {
    getTrips () {
      axios.get('http://127.0.0.1:8082/trip/?sort_by=discount&limit=4', {
        headers: {
          'Access-Control-Allow-Origin': '*',
          'Content-type': 'application/json',
        }
      })
      .then((response) => {
          return response["data"]
      })
      .then((data) => {
        this.triplistdiscount = data
      })
    },

    getBestTrip () {
      axios.get('http://127.0.0.1:8082/trip/?limit=3&sort_by=score', {
        headers: {
          'Access-Control-Allow-Origin': '*',
          'Content-type': 'application/json',
        }
      })
      .then((response) => {
          return response["data"]
      })
      .then((data) => {
        this.bestTrips = data
      })
    },

    getBlog () {
      axios.get('http://127.0.0.1:8082/blog/?limit=4', {
        headers: {
          'Access-Control-Allow-Origin': '*',
          'Content-type': 'application/json',
        }
      })
      .then((response) => {
          return response["data"]
      })
      .then((data) => {
        this.blogpost = data
      })
    },

    getReview () {
      axios.get('http://127.0.0.1:8082/review/', {
        headers: {
          'Access-Control-Allow-Origin': '*',
          'Content-type': 'application/json',
        }
      })
      .then((response) => {
          return response["data"]
      })
      .then((data) => {
        this.review = data
      })
    }
      
  },

  mounted () {
    this.getTrips();
    this.getBestTrip();
    this.getBlog();
    this.getReview();
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
/* STYLE PAGINA 1 */
.container-1{
  width: 100vw;
  height: 100vh;
  background-color: #fffbf3;
}
.header{
  height: 10vh;
  display: flex;
}
.row-1{
  display: flex;
  align-items: center;
  justify-content: center;
}
.logo{
  width: 7rem;
  height: 1.5rem;
}
.row-2{
  display: flex;
  align-items: center;
  justify-content: center;
}
.row-3{
  display: flex;
  justify-content: center;
  align-items: center;
  justify-content: space-evenly;
}
.login{
  color: darkorange;
  font-size: 1.2rem;
}
.button-signup{
  width: 7rem;
  height: 3rem;
  background-color: darkorange;
  color: white;
  font-size: 1.2rem;
  border: 0;
  border-radius: 5%;
}
.fila-2{
  height: 60vh;
  display: contents;
  justify-content: start; 
}
.colum-1{
  display: flex;
  flex-direction: column; 
  justify-content: center;
}
.titulo-1{
  font-size: 3rem;
  text-align: left;
  line-height: normal;
  font-weight: bold;
}
.parrafo-1{
  color: gray;
  font-size: 1.5rem;
  padding-bottom: 2rem;
  text-align: left;
}
.buttondiscover{
  background-color: white;
  color: darkorange;
  border: 0.1rem solid darkorange;
  height: 3.5rem;
  width: 10rem;
  border-radius: 5%;
  font-weight: bold; 
}
.imgtourist{
  height: 25rem;
  width: 20rem;
}
.colum-2{
  display: flex;
  align-items: center;
  justify-content: center;
}
.fila-3{
  height: 30vh;
  display: flex;
  justify-content: center;
  align-items: center;
}
.form{
  height: 10rem;
  width: 50rem;
  background-color: white;
  display: flex;
  align-items: center;
}
.buttonexplore{
  background-color: darkorange;
  color: white;
  border: 0;
  height: 4rem;
  width: 10rem;
  border-radius: 5%;
  font-weight: bold;
}
/* STYLE PAGINA 2 */
.container-2{
  width: 100vw;
  height: 100vh;
  background-color: #EEEEEE;
} 
.pag2-row1{
  height: 40vh;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
}
.title-pag2{
  font-size: 4rem;
  font-weight: bold;
}
.subtitle-pag2{
  font-size: 1.4rem;
  color: gray;
  width: 35rem;
}
.pag2-row2{
  height: 60vh;
}
.container-cards-pag2{
  height: 25rem;
  width: 100vw;
  display: flex;
  justify-content: center;
  align-items: center;
  justify-content: space-evenly;  
}
.style-card{
  width: 20rem;
  height: 20rem;
}
/* STYLE PAGINA 3 */
.container-3{
  height: 100vh;
  width: 100vw;
  background-color: #fffbf3;
}
.pag3-row1{
  height: 30vh;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
}
.title-pag3{
  font-size: 4rem;
  font-weight: bold;
}
.subtitle-pag3{
  font-size: 1.4rem;
  color: gray;width: 35rem;
}
.pag3-row2{
  height: 60vh;
}
.pag3-row3{
  height: 10vh;
  display: flex;
  align-items: center;
  justify-content: center;
}
/* STYLE PAGINA 4 */
.container-4{
  height: 100vh;
  width: 100vw;
  background-color: #fffbf3;
}
.pag4-row1{
  height: 30vh;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
}
.title-pag4{
  font-size: 4rem;
  font-weight: bold;
}
.subtitle-pag4{
  font-size: 1.4rem;
  color: gray;
  width: 40rem;
}
.pag4-row2{
  height: 10vh;
  justify-content: end;
}
.pag4-row3{
  height: 60vh;
}
/* STYLE PAGINA 5 */
.container-5{
  width: 100vw;
  height: 100vh;
  background-color:#EEEEEE;
}
.pag5-row1{
  height: 100vh; 
}
.title-pag5{
  font-size: 3.5rem;
  text-align: left;
  line-height: normal;
  font-weight: bold;
  padding-top: 10rem;
}
.subtitle-pag5{
  color: gray;
  font-size: 1.5rem;
  padding-bottom: 2rem;
  text-align: left;
}
.pag5-row1-col1{
  align-items: left;
  padding-top: 5rem;
}
.container-review{
  display: flex;
  justify-content: center;
  align-items: center;
}
.review{
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  width: 40rem;
  height: 25rem;
  background-color: #f6f6f6;
  position: relative;
}
.img-reviewer{
  width: 7rem;
  height: 7rem;
  border-radius: 50%;
  position: absolute;
  left: 0.8rem;
  top: 1rem;
}
.review-content{
  width: 30rem;
  height: 10rem;
  background-color: white;
  display: flex;
  align-items: center;
  padding-left: 2rem;
  padding-top: 1rem;
  text-align: left;
  border-top-right-radius: 1rem;
  border-top-left-radius: 1rem;
}
.name{
  width: 30rem;
  height: 5rem;
  display: flex;
  align-items: center;
  font-size: 1.1rem;
  font-weight: bold;
  background-color: white;
  padding-left: 2rem;
  border-bottom-left-radius: 1rem;
  border-bottom-right-radius: 1rem;
  box-shadow: 2px 4px 4px  rgb(177, 176, 176);
}
/* STYLE PAGINA 6 */
.container-6{
  width: 100vw;
  height: 100vh;
  background-color: #fffbf3;
}
.pag6-row1{
  height: 20vh;
  display: flex;
  justify-content: center;
  align-items: center;
}
.title-pag6{
  font-size: 4rem;
  font-weight: bold;
}
.pag6-row2{
  height: 70vh;
  display: flex;
  align-items: center;
}
.container-card-pag6{
  width: 20rem;
  height: 30rem;
}
/* STYLE PAGINA 7 */
.container-7{
  width: 100vw;
  height: 100vh;
  background-color: #EEEEEE;
}
.pag7-row1{
  height: 40vh;
  background-color: darkorange;
  border-radius: 1rem;
  display: flex;
  justify-content: center;
  align-items: center;
}
.title-pag7{
  color: white;
  width: 60vw;
  font-size: 3.5rem;
  font-weight: bold; 
  line-height: normal;
}
.form-group{
  display: flex; 
  width: 45vw; 
  height: 5rem; 
  align-items: center; 
  background-color: white; 
  border-radius: 0.5rem;
}
.img-email{
height: 2rem; 
width: 2rem; 
margin-left: 0.5rem;
}
.form-control{
  border: 0;
}
.button-suscribe{
  background-color: darkorange; 
  color: white; 
  border: 0; 
  height: 3.5rem; 
  width: 10rem; 
  border-radius: 0.2rem; 
  margin-right: 0.5rem;
}
.pag7-row2{
  height: 45vh;
}
.pag7-row2-col1{
  text-align: left;
  padding-top: 3rem;
}
.subtitle-pag7{
  width: 20vw; 
  color: gray; 
  font-size: 1.3rem; 
  line-height: normal; 
  padding-top: 2rem; padding-bottom: 1rem;
}
.img-socialnetwork{
  height: 2rem; 
  width: 2rem; 
  margin-left: 0.5rem; 
  margin-left: 0.5;
}
.pag7-row2-col2, .pag7-row2-col3, .pag7-row2-col4{
  text-align: left;
}
.company, .contact, .more{
  list-style-type:none; 
  font-size: 1.5rem; 
  margin-top: 4rem; 
  font-weight: bold;
}
.company-items, .contact-items, .more-items{
  list-style-type:none; 
  font-size: 1.5rem; 
  color: gray;
}
.pag7-row3{
  height: 15vh; 
  border-top: 0.1rem solid gray; 
  font-size: 1.3rem; 
  color: gray;
}
.pag7-row3-col1, .pag7-row3-col2{
  padding-top: 2rem
}
.copyrigth{
  text-align: left;
}
.condition{
  text-align: right;
}

</style>
