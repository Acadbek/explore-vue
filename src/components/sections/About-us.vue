<template>
  <div class="grid grid-cols-12">
    <main class="col-span-4">text</main>
    <main class="page col-span-8">
      <div class="container">
        <div class="circle-carousel" data-speed="2000" data-autoplay="2500">
          <div class="slides">
            <h2 v-for="(i, idx) in slides" :key="idx" class="slide">
              {{ i.id }}
            </h2>
          </div>
          <div class="pagination">
            <div v-for="(i, idx) in slides" :key="idx" class="item">
              <div class="dot">
                <span>{{ i.id }}</span>
              </div>
            </div>
          </div>
          <button class="next">next</button>
          <button class="prev">prev</button>
        </div>
      </div>
    </main>
  </div>
</template>

<script>
export default {
  data() {
    return {
      slides: [
        { id: 1 },
        { id: 2 },
        { id: 3 },
        { id: 4 },
        { id: 5 },
        { id: 6 },
        { id: 7 },
        { id: 8 },
        { id: 9 },
        { id: 10 },
        { id: 11 },
        { id: 12 },
        { id: 13 },
      ],
    };
  },
  mounted() {
    function initCarousel(options) {
      function CustomCarousel(options) {
        this.init(options);
        this.addListeners();
        return this;
      }

      CustomCarousel.prototype.init = function (options) {
        this.node = options.node;
        this.node.slider = this;
        this.slides = this.node.querySelector(".slides").children;
        this.slidesN = this.slides.length;
        this.pagination = this.node.querySelector(".pagination");
        this.pagTransf = "translate( -50%, -50% )";
        this.dots = this.pagination.children;
        this.dotsN = this.dots.length;
        this.step = -360 / this.dotsN;
        this.angle = 0;
        this.next = this.node.querySelector(".next");
        this.prev = this.node.querySelector(".prev");
        this.activeN = options.activeN || 0;
        this.prevN = this.activeN;
        this.speed = options.speed || 300;
        this.autoplay = options.autoplay || false;
        this.autoplayId = null;

        this.setSlide(this.activeN);
        this.arrangeDots();
        this.pagination.style.transitionDuration = this.speed + "ms";
        if (this.autoplay) this.startAutoplay();
      };

      CustomCarousel.prototype.addListeners = function () {
        var slider = this;

        if (this.next) {
          this.next.addEventListener("click", function () {
            slider.setSlide(slider.activeN + 1);
          });
        }

        if (this.prev) {
          this.prev.addEventListener("click", function () {
            slider.setSlide(slider.activeN - 1);
          });
        }

        for (var i = 0; i < this.dots.length; i++) {
          this.dots[i].addEventListener(
            "click",
            (function (i) {
              return function () {
                slider.setSlide(i);
              };
            })(i)
          );
        }

        if (this.autoplay) {
          this.node.addEventListener("mouseenter", function () {
            slider.stopAutoplay();
          });

          this.node.addEventListener("mouseleave", function () {
            slider.startAutoplay();
          });
        }
      };

      CustomCarousel.prototype.setSlide = function (slideN) {
        this.slides[this.activeN].classList.remove("active");
        if (this.dots[this.activeN])
          this.dots[this.activeN].classList.remove("active");

        this.prevN = this.activeN;
        this.activeN = slideN;
        if (this.activeN < 0) this.activeN = this.slidesN - 1;
        else if (this.activeN >= this.slidesN) this.activeN = 0;

        this.slides[this.activeN].classList.toggle("active");
        if (this.dots[this.activeN])
          this.dots[this.activeN].classList.toggle("active");

        this.rotate();
      };

      CustomCarousel.prototype.rotate = function () {
        if (this.activeN < this.dotsN) {
          this.angle += (function (dots, next, prev, step) {
            var inc,
              half = dots / 2;
            if (prev > dots) prev = dots - 1;
            if (Math.abs((inc = next - prev)) <= half) return step * inc;
            if (Math.abs((inc = next - prev + dots)) <= half) return step * inc;
            if (Math.abs((inc = next - prev - dots)) <= half) return step * inc;
          })(this.dotsN, this.activeN, this.prevN, this.step);

          this.pagination.style.transform =
            this.pagTransf + "rotate(" + this.angle + "deg)";
        }
      };

      CustomCarousel.prototype.startAutoplay = function () {
        var slider = this;

        this.autoplayId = setInterval(function () {
          slider.setSlide(slider.activeN + 1);
        }, this.autoplay);
      };

      CustomCarousel.prototype.stopAutoplay = function () {
        clearInterval(this.autoplayId);
      };

      CustomCarousel.prototype.arrangeDots = function () {
        for (var i = 0; i < this.dotsN; i++) {
          this.dots[i].style.transform =
            "rotate(" + (360 / this.dotsN) * i + "deg)";
        }
      };

      return new CustomCarousel(options);
    }

    // Init
    var plugins = {
      customCarousel: document.querySelectorAll(".circle-carousel"),
    };

    document.addEventListener("DOMContentLoaded", function () {
      if (plugins.customCarousel.length) {
        for (var i = 0; i < plugins.customCarousel.length; i++) {
          var carousel = initCarousel({
            node: plugins.customCarousel[i],
            speed: plugins.customCarousel[i].getAttribute("data-speed"),
            autoplay: plugins.customCarousel[i].getAttribute("data-autoplay"),
          });
        }
      }
    });
  },
};
</script>

<style lang="scss">
.circle-carousel {
  position: relative;
  padding-top: 100%;
  background: rgba(black, 0.3);

  .slides {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
  }

  .slide {
    display: flex;
    align-items: center;
    justify-content: center;
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: 0;
    opacity: 0;
    background: rgba(red, 0.3);

    &.active {
      z-index: 1;
      opacity: 1;
    }
  }

  .pagination {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    z-index: 1;
    width: 90%;
    height: 90%;
    border-radius: 50%;
    border: 3px solid white;
    transition-property: transform;
    transition-timing-function: ease-out;
    // transition-timing-function: cubic-bezier(.5,-.5,.5,1.5);
    pointer-events: none;
    user-select: none;

    .dot {
      display: flex;
      align-items: center;
      justify-content: center;
      position: absolute;
      top: 0;
      left: 50%;
      transform: translate(-50%, -50%);
      width: 50px;
      height: 50px;
      border-radius: 50%;
      pointer-events: auto;
      transition: 0.3s;
      background: black;

      &:hover {
        transform: translate(-50%, -50%) scale(1.05);
        cursor: pointer;
        background: white;
        color: black;
      }
    }

    .item {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      border-radius: 50%;

      &.active {
        .dot {
          background: white;
          color: black;
        }
      }
    }
  }

  .next,
  .prev {
    position: absolute;
    bottom: 6%;
    z-index: 1;
    font-size: 12px;
    text-transform: uppercase;
    letter-spacing: 0.3em;
    transition: 0.3s;
    user-select: none;

    &:before {
      content: "";
      position: absolute;
      top: 50%;
      z-index: -1;
      transform: translate(-50%, -50%);
      border-style: solid;
      border-color: transparent black;
      transition: 0.3s;
    }

    &:hover {
      cursor: pointer;
      color: black;

      &:before {
        border-color: transparent white;
        transform: translate(-50%, -50%) scale(1.05);
      }
    }
  }

  .next {
    right: 5%;

    &:before {
      left: 65%;
      border-width: 30px 0 30px 70px;
    }
  }

  .prev {
    left: 5%;

    &:before {
      left: 35%;
      border-width: 30px 70px 30px 0;
    }
  }
}
</style>
