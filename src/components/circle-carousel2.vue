<template>
  <div class="App">
    <button class="m-3 border-2 border-blue-400 px-2" @click="next">
      next
    </button>
    <button class="m-3 border-2 border-blue-400 px-2" @click="prev">
      prev
    </button>
    <div class="test">
      <div
        class="carousel"
        v-for="(item, index) in carousel.length"
        :key="index"
      >
        <div class="item-carousel">{{ item.name }} {{ "chi gap" }}</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      carouselDeg: 17,
      itemDeg: -17,
      centerItem: 0,
      prevItem: 9,
      lastItem: 9,
      nextItem: 1,
      carousel: [
        { name: "Jone", id: 0, position: 1 },
        { name: "Wong", id: 1, position: 2 },
        { name: "Kaylem", id: 2, position: 3 },
        { name: "Aila", id: 3, position: 4 },
        { name: "Amin", id: 4, position: 5 },
        { name: "Jannat", id: 5, position: 6 },
        { name: "Rohaan", id: 6, position: 7 },
        { name: "Malaki", id: 7, position: 8 },
        { name: "Kade", id: 8, position: 9 },
        { name: "Alex", id: 9, position: 10 },
      ],
    };
  },
  methods: {
    getID(side) {
      const prevNext = (itemID) => {
        if (itemID === this.lastItem) {
          this.nextItem = 0;
          this.prevItem = this.lastItem - 1;
        } else if (itemID === 0) {
          this.prevItem = this.lastItem;
          this.nextItem = 1;
        } else {
          this.nextItem = this.centerItem + 1;
          this.prevItem = this.centerItem - 1;
        }
      };

      if (side) {
        this.centerItem = this.nextItem;
        prevNext(this.centerItem);
      } else {
        this.centerItem = this.prevItem;
        prevNext(this.centerItem);
      }
    },
    next() {
      this.getID(true);
      this.carouselDeg = this.carouselDeg - 35;
      this.itemDeg = this.itemDeg + 35;
    },
    prev() {
      this.getID(false);
      this.carouselDeg = this.carouselDeg + 35;
      this.itemDeg = this.itemDeg - 35;
    },

    getCssClass(id) {
      const { centerItem, nextItem, prevItem } = this.carousel;
      if (id === centerItem) {
        return "active";
      } else if (id === nextItem) {
        return "next";
      } else if (id === prevItem) {
        return "prev";
      }
    },
  },
};
</script>

<style lang="scss">
.App {
  font-family: sans-serif;
  margin: 100px 200px;
}

.carousel {
  position: relative;
  width: 364px;
  height: 364px;
  border: 2px solid;
  border-radius: 50%;
  transition: 0.5s;
  // transform: rotate(15deg);
  transform-origin: center center;
}
// .test {
//   position: absolute;
//   left: 600px;
//   width: 20px;
//   height: 364px;
//   background: #000;

//   &:before {
//     content: '';
//     position: absolute;
//     width: 20px;
//     height: 20px;
//     background: red;
//     z-index: 1111;
//     top: 50%;
//     transform: translateY(-50%);
//   }
// }
.carousel::before {
  /* content: ""; */
  position: absolute;
  width: 50%;
  height: 100%;
  background: #000;
  border-radius: 50% 0 0 50%;
}
// с = 2 Pr
.item-carousel {
  position: absolute;
  border-radius: 50%;
  border: 1px solid red;
  background: #fff;
  width: 50px;
  height: 50px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 14px;
  margin: 2px;
  bottom: 0;
  transition: 0.5s;

  &.next {
    background: blue;
    color: white;
  }
  &.prev {
    background: green;
    color: white;
  }

  &.active {
    background: #000;
    color: white;
  }

  &:nth-child(1) {
    right: -19px;
    top: 101px;
  }
  &:nth-child(2) {
    right: -17px;
    top: 213px;
  }
  &:nth-child(3) {
    right: 49px;
    top: 303px;
  }
  &:nth-child(4) {
    right: 156px;
    top: 337px;
  }
  &:nth-child(5) {
    right: 263px;
    top: 302px;
  }
  &:nth-child(6) {
    right: 330px;
    top: 210px;
  }
  &:nth-child(7) {
    right: 330px;
    top: 100px;
  }
  &:nth-child(8) {
    right: 263px;
    top: 7px;
  }
  &:nth-child(9) {
    right: 156px;
    top: -27px;
  }
  &:nth-child(10) {
    right: 48px;
    top: 6px;
  }
}
</style>
