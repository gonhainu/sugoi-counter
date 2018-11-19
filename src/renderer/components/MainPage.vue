<template>
  <div class="container">
    <img id="frame" src="static/HW_sugoisystem_181115.jpg" />
    <div class="counter">
      {{ counter }}
    </div>
    <div class="counter--shadow">
      {{ counter }}
    </div>
    <div>
      <img id="sugoi-logo" class="sugoi-logo" src="static/sugoi_logo.svg"/>
    </div>
    <audio id="audio--sugoi1" >
      <source src="static/sounds/sugoi-1.mp3" />
    </audio>
    <audio id="audio--sugoi2">
      <source src="static/sounds/sugoi-2.mp3" />
    </audio>
    <audio id="audio--sugoi3">
      <source src="static/sounds/sugoi-3.mp3" />
    </audio>
    <audio id="audio--sugoi4">
      <source src="static/sounds/sugoi_2-1.mp3" />
    </audio>
    <audio id="audio--sugoi5">
      <source src="static/sounds/sugoi_2-2.mp3" />
    </audio>
    <audio id="audio--sugoi6">
      <source src="static/sounds/sugoi_2-3.mp3" />
    </audio>
    <audio id="audio--sugoi7">
      <source src="static/sounds/sugoi_2-4.mp3" />
    </audio>
  </div>
</template>

<script>
  import anime from 'animejs';
  export default {
    name: 'MainPage',
    data() {
      return {
        counter: 0,
      };
    },
    mounted() {
      const elem = document.getElementById('sugoi-logo');
      const voice = document.getElementById('audio--sugoi5');
      const voice2 = document.getElementById('audio--sugoi7');
      window.addEventListener('keyup', (event) => {
        if (event.keyCode === 13) {
          this.counter += 1;
          const rnd = Math.floor(Math.random() * 10);
          if (rnd === 0) {
            voice.currentTime = 0;
            voice2.currentTime = 0;
            voice2.play();
          } else {
            voice.currentTime = 0;
            voice.play();
          }
          anime({
            targets: elem,
            scale: [
              {
                value: 1.25,
                duration: 100,
              },
              {
                value: 1,
                duration: 100,
              },
            ],
          });
        }
      });
    },
  };
</script>

<style lang="scss" scoped>
  $font_size: 250px;
  .container {
    width: 1920px;
    height: 1080px;
    position: relative;
    overflow: hidden;
  }
  #frame {
    width: 1920px;
    height: 1080px;
    position: absolute;
    top: 0;
    left: 0;
  }
  .counter {
    position: absolute;
    top: 420px;
    left: 50%;
    transform: translate(-50%, 0);
    color: #fdc825;
    font-size: $font_size;
    font-family: "Drifter-Five", "DrifterFiveAl";
  }
  .counter--shadow {
    position: absolute;
    top: calc(420px + 25px);
    left: 50%;
    transform: translate(calc(-50% + 25px), 0);
    color: #fdc825;
    opacity: 0.20;
    font-size: $font_size;
    font-family: "Drifter-Five", "DrifterFiveAl";
  }
  .sugoi-logo {
    position: absolute;
    right: 100px;
    top: 740px;
    height: 320px;
    /*-webkit-transform-style: preserve-3d;*/
    -webkit-transform: translate3d(0, 0, 0);
  }
</style>
