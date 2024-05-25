<template>
  <header :style="backgroundStyle" class="p-10 w-full h-[850px] bg-cover bg-no-repeat relative flex flex-col justify-center items-center">
    <div class="absolute top-0 left-0 right-0 lg:py-8 xs:py-4 sm:py-4 lg:px-16 sm:px-6 xs:px-6 flex justify-between">
      <img class="cursor-pointer sm:w-16 xs:w-12" src="./assets/logo.svg" alt="">
      <button class="chat-button sm:py-[8px] sm:px-4 xs:px-2 xs:py-1 xs:text-[14px] lg:text-base"><a href="https://wa.me/message/DMNVYF4VDRVZK1">Chat with us</a></button>
    </div>
    <div class="flex flex-col items-center text-[#FEFEFE]">
      <span class="font-normal lg:text-[80px] xs:text-[30px]">Sheela styles</span>
      <span class="font-normal lg:text-xl xs:text-[15px]">Solemnly made</span>
    </div>
  </header>

  <div class="xl:mx-[2rem] 2xl:mx-[10rem] sm:mx-4 xs:mx-4">
    <div class="flex sm:gap-5 xs:gap-4 justify-center align-middle items-start lg:my-16 sm:my-7 xs:my-8">
      <div class="flex sm:gap-4 xs:gap-2 xs:w-[70%] sm:w-[26%] lg:w-[25%] xl:w-[9.8%]">
        <span id="about" class="font-normal xs:text-[12px] sm:text-sm lg:text-base xl:text-xl">About us</span>
        <img class="xs:w-4 sm:w-[40px]" src="./assets/arrow.svg" alt="" loading="lazy">
      </div>
      <div>
        <p class="xl:w-[1090px] sm:text-sm md:text-base lg:text-xl xl:text-5xl font-normal">Sheela styles is where sustainability meets craftmanship in every stitch. Crafted with care by skilled artisans, our garments showcase the rich heritage of Ankara prints.</p>
      </div>
    </div>
    <div class="flex sm:gap-16 xs:gap-2 justify-center lg:mb-16">
      <img class="xl:w-[580px] lg:w-[455px] sm:w-[300px] xs:w-[200px] sm:mt-20 xs:mt-5" src="./assets/Canon0130.jpg" alt="" loading="lazy">
      <img class="xl:w-[580px] lg:w-[455px] sm:w-[300px] xs:w-[200px] sm:mb-20 xs:mb-5" src="./assets/Canon0062.jpg" alt="" loading="lazy">
    </div>
    <div class="flex sm:gap-5 xs:gap-5 justify-center align-middle items-start lg:my-16 sm:my-7 xs:my-8">
      <div class="flex sm:gap-4 xs:gap-1 xs:w-[60%] sm:w-[40%] lg:w-[25%] xl:w-[13%]">
        <span id="selected-styles" class="font-normal xs:text-[10px] sm:text-sm lg:text-base xl:text-xl">Selected styles</span>
        <img class="xs:w-4 sm:w-[40px]" src="./assets/arrow.svg" alt="">
      </div>
      <div>
        <p class="xl:w-[1030px] sm:text-sm md:text-base lg:text-xl xl:text-5xl font-normal">Whether you’re dressing up for a special occasion or adding a pop of color to your everyday look, we have something for every fashionista.</p>
      </div>
    </div>
    <div>
      <div class="flex justify-center sm:mb-10 xs:mb-3">
        <div class="">
          <img class="xl:w-[690px] lg:w-[540px] sm:w-[400px] xs:w-[220px] sm:mb-10 xs:mb-3"src="./assets/Canon0206.jpg" alt="" loading="lazy">
          <img class="xl:w-[834px] lg:w-[700px] sm:w-[600px] xs:w-[320px]"src="./assets/Canon00541.jpg" alt="" loading="lazy">
        </div>
        <div class="">
          <div class="sm:mb-10 xs:mb-4">
            <img class="xl:w-[430px] lg:w-[380px] sm:w-[300px] xs:w-[180px]"src="./assets/Canon04211.jpg" alt="" loading="lazy">
          </div>
          <div class="flex justify-end">
            <img class="xl:w-[332px] lg:w-[250px] sm:w-[180px] xs:w-[110px]"src="./assets/Canon016711.jpg" alt="" loading="lazy">
          </div>
        </div>
      </div>
      <div class="flex lg:gap-[10.3rem] sm:gap-20 xs:gap-10 justify-center">
        <div> 
          <img class="sm:w-[486px] xs:w-[350px]"src="./assets/Canon05041.jpg" alt="" loading="lazy">
        </div>
        <div>
          <img class="sm:w-[610px] xs:w-[410px]"src="./assets/Canon0432.jpg" alt="" loading="lazy">
        </div>
      </div>
    </div>
    <div class="flex sm:gap-5 xs:gap-10 justify-center align-middle items-start lg:mt-20 lg:mb-16 sm:mt-8 sm:mb-6 xs:mt-5 xs:mb-3">
      <div class="flex sm:gap-4 xs:gap-2">
        <span id="sustainability" class="font-normal xs:text-[10.5px] sm:text-base xl:text-xl">Sustainability</span>
        <img class="xs:w-4 sm:w-[40px]" src="./assets/arrow.svg" alt="">
      </div>
      <div>
        <p class="xl:w-[1080px] sm:text-sm md:text-base lg:text-xl xl:text-5xl font-normal">Shella is committed to investing more into our environment sustainability.</p>
      </div>
    </div>
    <div class="flex sm:gap-7 xs:gap-2 items-center justify-center sm:mb-20 xs:mb-10">
      <img class="xl:w-[475.5px] lg:w-[400px] sm:w-[280px] xs:w-[140px]"src="./assets/Canon02921.jpg" alt="" loading="lazy">
      <img class="xl:w-[475.5px] lg:w-[324px] sm:w-[226px] xs:w-[115px]" src="./assets/Frame15.jpg" alt="" loading="lazy">
      <p class="font-normal sm:text-xl xs:text-[6.3px]">We source eco-friendly fabrics to reduce waste through innovative design process, we prioritize quality and sustainability at every step.</p>
    </div>
  </div>
  <footer class="bg-[#010101] text-[#FEFEFE] xl:px-[2rem] 2xl:px-[10rem] lg:py-[4rem] sm:py-6 sm:px-4 xs:py-10 xs:px-4">
    <div class="sm:flex sm:gap-12">
      <img class="xl:w-[440px] lg:w-[360px] sm:w-[200px] xs:w-[398px]"src="./assets/Canon003511.jpg" alt="" loading="lazy">
      <div class="xs:mt-6 sm:mt-0">
        <div class="font-normal sm:text-xl xs:text-[20px]">Menu</div>
        <div class="flex flex-col xl:gap-[17.5rem] lg:gap-[14.5rem] sm:gap-[6rem] xs:gap-[3.3rem]">
          <div class="flex flex-wrap sm:gap-10 xs:gap-5 font-normal xl:text-[32px] sm:text-[20px] xs:text-[24px]">
            <a href="#about">About</a>
            <a href="#selected-styles">Selected styles</a>
            <a href="#sustainability">Sustainability</a>
            <a href="https://wa.me/message/DMNVYF4VDRVZK1">Chat with us</a>
          </div>
          <div class="font-normal xl:text-2xl sm:text-lg xs:text-[20px] flex sm:flex-row xs:flex-col sm:gap-6 xs:gap-2">
            <span>Call us: +44 7957 279873</span>
            <span>Email us: sales.sheelastyles@gmail.com</span>
          </div>
        </div>
      </div>
    </div>
  </footer>
</template>

<script>
import heroImage1 from './assets/heroImage1.jpg';
import heroImage2 from './assets/heroImage2.jpg';
import heroImage3 from './assets/heroImage3.jpg';

export default {
  name: 'App',
  data() {
    return {
      images: [heroImage1, heroImage2, heroImage3],
      currentImageIndex: 0,
    };
  },
  computed: {
    backgroundStyle() {
      return {
        backgroundImage: `url(${this.images[this.currentImageIndex]})`,
      };
    },
  },
  mounted() {
    this.startImageRotation();
  },
  methods: {
    startImageRotation() {
      setInterval(() => {
        this.currentImageIndex = (this.currentImageIndex + 1) % this.images.length;
      }, 2000);
    },
  },
};
</script>

<style scoped>
/* Add transition to the background image */
header {
  transition: background-image 1s ease-in-out;
}

/* Footer link hover effect */
footer a {
  position: relative;
  color: #FEFEFE;
  text-decoration: none;
  display: inline-block;
}

footer a::after {
  content: '';
  position: absolute;
  width: 100%;
  transform: scaleX(0);
  height: 2px;
  bottom: -2px;
  left: 0;
  background-color: #FEFEFE;
  transform-origin: bottom right;
  transition: transform 0.25s ease-out;
}

footer a:hover::after {
  transform: scaleX(1);
  transform-origin: bottom left;
}

/* Chat button styles */
.chat-button {
  background-color: #010101;
  color: #FEFEFE;
  transition: background-color 0.3s, transform 0.1s;
}

.chat-button:active {
  background-color: #333333;
  transform: scale(0.95);
}

@media (max-width: 1024px) {
  header {
    height: 600px;
  }
  body {
    overflow: hidden;
  }
}

@media (max-width: 768px) {
  header {
    height: 400px;
  }
}

@media (max-width: 480px) {
  header {
    height: 300px;
  }
}

@media (max-width: 425px) {
  header {
    height: 500px;
  }
}
</style>
