<template>
  <div class="feature-style-2 bg-cover section live-footer">
    <!-- <h1 class="title header-content2">FUSION</h1> -->

    <div class="container">
      <div class="row">
        <div class="col-8 mx-auto">
          <div class="screenshot-gallery text-center">
            <img
              src="../assets/img/wf0x/feature/L4.png"
              alt="screenshot thumb"
              style="height:400px;"
            />
          </div>
        </div>
      </div>
      <div class="header-content text-center">
        <h2 style="color:white;">FUSION</h2>
      </div>
      <br />
      <div class="row">
        <div class="col-10 mx-auto">
          <div class="text-center">
            <p class="header-detail text-center">
              <span><img src="../assets/img/icon/Asset5.png"/></span> Game
              tournament is win-lose by game formula(addition current
              performance if any). There are weekly, monthly, world tournaments
              and grouping users in different groups based on their strength.
              <span><img src="../assets/img/icon/Asset4.png"/></span>
            </p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "GameTournament",
  data() {
    return {
      bgImg: {
        backgroundImage: `url(${require("../assets/img/bg/screenshot-bg.jpg")})`,
      },
      swiperOption: {
        speed: 600,
        loop: true,
        slidesPerView: 3,
        effect: "coverflow",
        // grabCursor: true,
        centeredSlides: true,
        coverflowEffect: {
          rotate: -25,
          stretch: 0,
          depth: 100,
          modifier: 1,
          slideShadows: false,
        },
        navigation: {
          nextEl: ".swiper-button-next",
          prevEl: ".swiper-button-prev",
        },
        breakpoints: {
          768: {
            spaceBetween: 60,
          },
          576: {
            slidesPerView: 2,
            spaceBetween: 20,
          },
        },
      },
    };
  },
};
</script>
