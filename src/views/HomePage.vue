<template>
  <ion-page>
    <ion-header :translucent="true">
      <ion-toolbar>
        <ion-title  style="background-color: #fc810f; padding: 18px;">
          
        <div style="font-size: 28px">
          <b>
            <ion-text
              >Chess</ion-text
            >
            <ion-text style="color: white;" 
              >Tutor</ion-text
            >
            <ion-text
              >AI</ion-text
            >
          </b>
        </div>
        </ion-title>
      </ion-toolbar>
    </ion-header>

    <ion-content :fullscreen="true">


      <div id="container">
        <div class="center-container">
    <div
      id="carouselExampleIndicators"
      class="carousel slide swiper-carousel"
      data-bs-ride="carousel"
    >
      <div class="carousel-indicators">
        <button
          v-for="(slide, index) in builder"
          :key="index"
          type="button"
          :data-bs-target="'#carouselExampleIndicators'"
          :data-bs-slide-to="index"
          :class="{ active: index === 0, 'indicator-circle': true }"
          aria-current="true"
          :aria-label="'Slide ' + (index + 1)"
        ></button>
      </div>
      <div class="carousel-inner">
        <div
          v-for="(slide, index) in builder"
          :key="index"
          :class="{ 'carousel-item': true, active: index === 0 }"
        >
          <div
            class="position-absolute top-50 start-0 w-100 translate-middle-y"
          >
            <div class="container">
              <div class="info text-white text-start">
                <h1 class="text-white">
                  {{   slide.name }}
                </h1>
                <router-link :to="slide.url">
                  <!--
                  <button
                    class="btn-landing"
                    :id="'learn-button-' + index"
                    @click="navigateToLearn(slide, index)"
                  >
                  {{ $t("carousel_slide" + (index + 1) + "_button") }}
                  </button>
                    
                  
                  -->
                </router-link>
              </div>
            </div>
          </div>
          <img :src="slide.imageUrl" class="d-block mx-auto" />
        </div>
      </div>
    </div>
  </div>
      </div>
    </ion-content>
  </ion-page>
</template>

<script>

import { IonContent, IonHeader, IonPage, IonTitle, IonToolbar,IonText } from '@ionic/vue';

export default {
  name: "Carousel",
  components: {
    IonContent,
    IonHeader,
    IonPage,
    IonTitle,
    IonToolbar,
    IonText
  },
  data() {
    return {
      builder: [
        {
          name: "Learn using ChessTutorAI's optimized e-book collection",
          button: "Go to Catalog",
          url: "/",
          imageUrl: "/images/landing/landing_img1.jpg",
        },
        {
          name: "Learn with ChessTutorAI reading e-book",
          button: "Go to Learn",
          url: "/",
          imageUrl: "/images/landing/landing_img2.jpeg",
        },
        {
          name: "Practice with customized training program",
          button: "Go to Practice",
          url: "/",
          imageUrl: "/images/landing/landing_img3.jpg",
        },
      ],
    };
  },
  methods: {
    navigateToLearn(slide, index) {
      if (index === 1) {
        this.pgnfree =
          "1. e4 e5 2. Nf3 Nc6 3. Nc3 Nf6 4. Bb5 Bb4 5. O-O O-O 6. d3 d6 7. Bg5 Bxc3 8. bxc3 Bd7";
        this.$store.dispatch("setPgn", this.pgnfree);
        this.$router.push({ name: "chessviewer" });
      }
    },
  },
};
</script>

<style scoped>
.center-container {
  width: 100%;
  height: 100%;
  overflow-x: hidden;
}
.carousel-container {
  width: 100%;
  overflow: hidden;
}
.carousel-inner {
  width: 100%;
}
.carousel-inner .carousel-item {
  width: 100%;
}
.carousel-inner img {
  max-width: 100%;
  width: 100%;
  height: 100vh;
  object-fit: cover;
}
.container {
  width: 100%;
  margin-top: 15%;
}

.info {
  width: 100%;
  margin-left: 0px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
.info h1 {
  font-size: 50px;
  font-weight: 600;
  word-wrap: break-word;
}
.btn-landing {
  margin-top: 60%;
  background-color: #d9d9d9;
  color: black;
  border-radius: 30px;
  padding: 10px 30px;
  font-size: 20px;
  font-weight: 500;
  border: none;
  cursor: pointer;
  transition: all 0.3s ease;
  box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.3);
}
.btn-landing:hover {
  background-color: white;
  color: black;
  box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.7);
}
.carousel-indicators .indicator-circle {
  width: 15px;
  height: 15px;
  border-radius: 50%;
  background-color: white;
  opacity: 1;
  box-shadow: rgba(0, 0, 0, 0.7);
  margin-right: 10px;
  cursor: pointer;
  border: none;
  outline: none;
}
.carousel-indicators .indicator-circle.active {
  background-color: #18b41e;
  box-shadow: none;
}

.carousel-control-prev,
.carousel-control-next {
  margin-left: -30px;
  margin-right: -20px;
}
</style>

