<template>
  <header class="header-main header-main2" :class="{ sticky: scrolled }">
    <div class="container">
      <div class="row">
        <div class="col-12">
          <div class="menu-wrap">
            <div class="brand-logo">
              <a href="#">
                <img
                  src="../assets/img/wf0x/Logo_Twitter.png"
                  alt="Brand Logo"
                  class="wflogo"
                />
              </a>
            </div>
            <div id="hamburger" v-on:click="display_menu()">
              <span></span>
              <span></span>
              <span></span>
            </div>
            <ul class="main-menu main-menu__style-2">
              <li>
                <a v-on:click="close_menu()" href="#home" class="activee"
                  >Home</a
                >
              </li>
              <li><a v-on:click="close_menu()" href="#feature">Feature</a></li>
              <li>
                <a v-on:click="close_menu()" href="#character">Character</a>
              </li>
              <li><a v-on:click="close_menu()" href="#roadmap">Road Map</a></li>
              <li><a v-on:click="close_menu()" href="#tokenView">Token</a></li>
              <li><a v-on:click="close_menu()" href="#wfteam">Team</a></li>
              <li>
                <a
                  v-on:click="newTab('https://docs.fantasy0x.com/')"
                  href="#wfteam"
                  >whitepaper</a
                >
              </li>
              <li class="mini-play d-lg-none">
                <a @click="goTo('/coming-soon')">Play</a>
              </li>
            </ul>
            <button
              @click="goTo('/coming-soon')"
              class="play-btn main-menu__style-2 d-none d-lg-block mini-play"
            >
              PLAY
            </button>
          </div>
        </div>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  name: "Navbar",
  data() {
    return {
      load: false,
      limitPosition: 200,
      scrolled: false,
      lastPosition: 500,
    };
  },
  methods: {
    goTo: function(url) {
      this.$router.push(url);
    },
    newTab: function(url) {
      window.open(url, "_blank");
      this.close_menu();
    },
    // responsive menu script
    display_menu: function() {
      var body = document.getElementsByTagName("body")[0];
      !body.classList.contains("display_menu")
        ? body.classList.add("display_menu")
        : body.classList.remove("display_menu");
    },
    close_menu: function() {
      var body = document.getElementsByTagName("body")[0];
      body.classList.remove("display_menu");
    },
    loaded: function() {
      document.getElementsByTagName("body")[0].style.overflowY = "hidden";
      this.load = true;
    },

    // sticky menu script
    handleScroll() {
      if (
        this.lastPosition < window.scrollY &&
        this.limitPosition < window.scrollY
      ) {
        this.scrolled = true;
        // move up!
      }

      if (this.lastPosition > window.scrollY) {
        this.scrolled = true;
        // move down
      }

      this.lastPosition = window.scrollY;
      this.scrolled = window.scrollY > 50;
    },
  },
  created() {
    window.addEventListener("scroll", this.handleScroll);
  },
  destroyed() {
    window.removeEventListener("scroll", this.handleScroll);
  },

  mounted() {
    (function() {
      scrollTo();
    })();

    function scrollTo() {
      const links = document.querySelectorAll("a");
      links.forEach((each) => (each.onclick = scrollAnchors));
    }

    function scrollAnchors(e, respond = null) {
      const distanceToTop = (el) => Math.floor(el.getBoundingClientRect().top);
      e.preventDefault();
      var targetID = respond
        ? respond.getAttribute("href")
        : this.getAttribute("href");
      const targetAnchor = document.querySelector(targetID);
      if (!targetAnchor) return;
      const originalTop = distanceToTop(targetAnchor);
      window.scrollBy({ top: originalTop - 75, left: 0, behavior: "smooth" });
      const checkIfDone = setInterval(function() {
        const atBottom =
          window.innerHeight + window.pageYOffset >=
          document.body.offsetHeight - 0;
        if (distanceToTop(targetAnchor) === 0 || atBottom) {
          targetAnchor.tabIndex = "-1";
          targetAnchor.focus();
          clearInterval(checkIfDone);
        }
      }, 800);
    }
    //scroll spy js
    window.addEventListener("load", function() {
      var section = document.querySelectorAll(".main-container > *");
      var sections = {};
      var i = 0;

      Array.prototype.forEach.call(section, function(e) {
        sections[e.id] = e.offsetTop - 85;
      });

      window.onscroll = function() {
        var scrollPosition =
          document.documentElement.scrollTop || document.body.scrollTop;
        for (i in sections) {
          if (i && i.length > 1 && sections[i] <= scrollPosition + 120) {
            document.querySelector(".activee").setAttribute("class", " ");
            document
              .querySelector("a[href*=" + i + "]")
              .setAttribute("class", "activee");
          }
        }
      };
    });
  },
};
</script>

<style lang="scss">
@import "../assets/scss/variables.scss";
@import "../assets/scss/components/header.scss";
.wflogo {
  height: 120px;
  // background: rgb(2, 0, 36);
  // background: linear-gradient(
  //   0deg,
  //   rgba(2, 0, 36, 1) 0%,
  //   rgba(9, 9, 121, 1) 0%,
  //   rgba(205, 0, 255, 1) 100%
  // );
}
.mini-play {
  background: linear-gradient(
    90deg,
    rgb(51, 139, 211) 5%,
    rgb(170, 91, 163) 100%
  );
  color: white !important;
}
.play-btn {
  text-align: center;
  cursor: pointer;
  color: black;
  padding: 15px 60px;
  font-size: large;
  align-self: center;
  border-radius: 25px;
  font-weight: bolder;
  color: white !important;
}
// .brand-logo {
//   align-self: start;
// }
</style>
