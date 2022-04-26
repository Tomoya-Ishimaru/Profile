<template>
  <div class="hobby-content">
    <div class="img-block">
      <div class="img-title observe_element">I love tennis</div>
      <img
        class="img-item"
        alt="Vue logo"
        src="../assets/images2/tennis.jpeg"
      />
    </div>
    <div class="img-block">
      <div class="img-title observe_element">I love baseball</div>
      <img
        class="img-item"
        alt="Vue logo"
        src="../assets/images2/baseball.jpeg"
      />
    </div>
    <!-- <div class="img-block">
      <div class="img-title">I love beautiful...</div>
      <img
        class="img-item"
        alt="Vue logo"
        src="../assets/images2/fireFlower.jpeg"
      />
    </div> -->

    <section class="carousel">
      <div class="carousel__main">
        <transition name="active">
          <div
            class="carousel__main"
            :key="images[active].id"
            v-show="active === images[active].id"
          >
          <div class="carousel__title">I love beautiful...</div>
            <img :src="images[active].img" />
          </div>
        </transition>
      </div>
      <div @click="prev" class="carousel__prev">
        <i class="fas fa-angle-left fa-5x"></i>
      </div>
      <div @click="next" class="carousel__next">
        <i class="fas fa-angle-right fa-5x"></i>
      </div>
      <!-- <ul class="carousel__thumbnails">
        <li
          v-for="(image) in images"
          :key="image.id"
          :class="{ current: active === image.id }"
          @click="current(image.id)"
        >
          <img :src="image.img" />
        </li>
      </ul> -->
    </section>
  </div>
</template>
<script>
export default {
  // name: 'Hobby',
  observe: {
    observer: null,
  },
 
  data(){
        return {
          active: 0,
          images: [
            {id:0, img:'images/sakura.jpeg'},
            {id:1, img:'images/fireFlower.jpeg'},
            {id:2, img:'images/kyoto2.jpeg'},
            {id:3, img:'images/snow.jpeg'},
            // {id:4, img:'images/flower.jpeg'},
            // {id:5, img:'images/image005.jpg'},
            // {id:6, img:'images/image006.jpg'},
          ]
        }
      },
  
  methods: {
    current(id) {
      this.active = id;
    },
    prev() {
      if (this.active <= 0) {
        this.active = this.images.length - 1;
      } else {
        this.active--;
      }
    },
    next() {
      if (this.active >= this.images.length - 1) {
        this.active = 0;
      } else {
        this.active++;
      }
    },
  },
  mounted() {
    // let that = this;
    // setInterval(() => {
    //   that.next();
    // }, 8000);

    this.observer = new IntersectionObserver(
      (entries) => {
        const entry = entries[0];
        if (entry && entry.isIntersecting) {
          console.log("画面に入ったよ");
          // console.log(entry.target.classList);
          entry.target.classList.add("inview");
          this.observer.unobserve(entry.target);
        }
      },
      {
        root: null,
        rootMargin: "-30%",
        threshold: 0,
        once: true,
      }
    );

    const observe_element = document.querySelectorAll(".img-title",".carousel__title");
    observe_element.forEach((el) => this.observer.observe(el));
    // const observe_element2 = document.querySelector(".carousel__title");
    // this.observer.observe(observe_element2);
  },
};
</script>
