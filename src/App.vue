<template>
  <div class="w-[99.1vw] h-[235vh] bg-gray-700">
    <div class="bg-gray-700 h-[60px] flex items-center fixed top-0 w-[100vw] border-b-[1px] border-gray-500 z-50">
      <span class="text-gray-100 font-semibold text-xl pl-[40px]">Naum</span>
      <div class="flex p-1 mt-1">
        <a href="https://www.tiktok.com/@naummdgames?lang=en" target="_blank"
          class="flex items-center justify-center w-8 h-8 bg-gray-300 rounded-full shadow-md hover:shadow-lg transition m-1">
          <img src="/src/assets/images/tiktok.avif" alt="TikTok" class="w-2/3 h-auto mt-[1px] mr-[0.5px]">
        </a>

        <a href="https://www.instagram.com/naummd/?hl=en" target="_blank"
          class="flex items-center justify-center w-8 h-8 bg-gray-300 rounded-full shadow-md hover:shadow-lg transition m-1">
          <img src="/src/assets/images/instagram.avif" alt="Instagram" class="w-2/3 h-auto mt-[1px] mr-[0.5px]">
        </a>

        <a href="https://x.com/Naummd1" target="_blank"
          class="flex items-center justify-center w-8 h-8 bg-gray-300 rounded-full shadow-md hover:shadow-lg transition m-1">
          <img src="/src/assets/images/twitter.avif" alt="Twitter" class="w-2/3 h-auto mt-[1px] mr-[1px]">
        </a>
      </div>
    </div>
    <div class="pt-[60px] overflow-hidden bg-[#0e0e0f] relative">
      <img src="/src/assets/images/mainbackdrop.avif" class="-ml-[170px] relative z-20" width="80%">
      <img src="/src/assets/images/mainbackdrop.avif" class="ml-[380px] absolute top-[60px] z-10" width="80%">
      <div
        class="absolute z-30 bg-gray-700 top-[55%] left-[62%] transform -translate-x-1/2 -translate-y-1/2 w-[650px] h-[475px] flex flex-col justify-center items-center rounded-[20px] border-[1px] border-gray-600">
        <img src="/src/assets/images/nunuw.webp"
          class="absolute top-0 left-0 w-full h-full object-cover rounded-[20px] z-10 opacity-50" />
        <div class="relative z-20 flex flex-col items-center">
          <span class="text-[80px] text-gray-100 font-[UMReg]">Welcome</span>
          <span class="text-gray-200 font-[NunitoSans]">· To Naummd's Editing portfolio ·</span>
        </div>
      </div>
    </div>
    <div class="pt-[40px]">
      <div>
        <span class="text-gray-200 font-[NunitoSans] text-[60px] ml-[300px]">My Work</span>
      </div>
      <div class="flex justify-center gap-8 px-[200px]">
        <div v-for="item in workitems" class="p-3 relative w-[460px]">
          <video class="w-full h-[300px] object-cover rounded-md" :src="item.video" muted loop
            @mouseover="$event.target.play()" @mouseleave="handleMouseLeave($event, item)" @play="item.isPlaying = true"
            @pause="item.isPlaying = false">
          </video>
          <div v-show="!item.isPlaying"
            class="absolute top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2 text-white bg-black bg-opacity-40 rounded-full p-2">
            <svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 24 24" fill="white"
              class="opacity-75">
              <path d="M8 5v14l11-7z" />
            </svg>
          </div>
          <span class="text-gray-200 font-semibold text-[22px] mt-2 block pl-2 font-[NunitoSans]">{{ item.name }}</span>
        </div>
      </div>
    </div>
    <div class="pt-[100px]">
      <div>
        <span class="text-gray-200 font-[NunitoSans] text-[60px] ml-[500px]">Video Showcase</span>
      </div>
      <div class="flex justify-center mt-8">
        <div class="relative w-[1000px]">
          <video ref="showcaseVideo" :src="workitems[1].video" class="w-full h-[550px] object-cover rounded-lg" autoplay
            loop muted @loadedmetadata="$refs.showcaseVideo.play()"></video>

          <!-- Volume Controls -->
          <div
            class="absolute bottom-4 right-4 flex items-center gap-2 bg-black bg-opacity-50 opacity-[0.85] p-2 rounded-lg">
            <!-- Mute/Unmute Button -->
            <button @click="toggleMute" class="text-white p-2 hover:bg-gray-700 rounded-full">
              <svg v-if="!isMuted" xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24"
                fill="white">
                <path
                  d="M3 9v6h4l5 5V4L7 9H3zm13.5 3c0-1.77-1.02-3.29-2.5-4.03v8.05c1.48-.73 2.5-2.25 2.5-4.02zM14 3.23v2.06c2.89.86 5 3.54 5 6.71s-2.11 5.85-5 6.71v2.06c4.01-.91 7-4.49 7-8.77s-2.99-7.86-7-8.77z" />
              </svg>
              <svg v-else xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="white">
                <path
                  d="M16.5 12c0-1.77-1.02-3.29-2.5-4.03v2.21l2.45 2.45c.03-.2.05-.41.05-.63zm2.5 0c0 .94-.2 1.82-.54 2.64l1.51 1.51C20.63 14.91 21 13.5 21 12c0-4.28-2.99-7.86-7-8.77v2.06c2.89.86 5 3.54 5 6.71zM4.27 3L3 4.27 7.73 9H3v6h4l5 5v-6.73l4.25 4.25c-.67.52-1.42.93-2.25 1.18v2.06c1.38-.31 2.63-.95 3.69-1.81L19.73 21 21 19.73l-9-9L4.27 3zM12 4L9.91 6.09 12 8.18V4z" />
              </svg>
            </button>

            <!-- Volume Slider -->
            <input type="range" min="0" max="1" step="0.05" v-model="volume" @input="updateVolume" class="w-24">
          </div>
        </div>
      </div>
    </div>
    <div class="flex justify-center mt-[100px]">
      <div class="m-1">
        <a href="https://www.tiktok.com/@naummdgames?lang=en" target="_blank"
          class="flex items-center justify-center w-10 h-10 bg-gray-300 rounded-full shadow-md hover:shadow-lg transition  m-1">
          <img src="/src/assets/images/tiktok.avif" alt="TikTok" class="w-2/3 h-auto">
        </a>

        <a href="https://www.instagram.com/naummd/?hl=en" target="_blank"
          class="flex items-center justify-center w-10 h-10 bg-gray-300 rounded-full shadow-md hover:shadow-lg transition  m-1">
          <img src="/src/assets/images/instagram.avif" alt="Instagram" class="w-2/3 h-auto">
        </a>

        <a href="https://x.com/Naummd1" target="_blank"
          class="flex items-center justify-center w-10 h-10 bg-gray-300 rounded-full shadow-md hover:shadow-lg transition  m-1">
          <img src="/src/assets/images/twitter.avif" alt="Twitter" class="w-2/3 h-auto">
        </a>
      </div>
      <div class="text-gray-300 font-semibold">
        <span class="block mt-[25px]">+1 647(745) 9455</span>
        <span class="block mt-[10px]">naum.dimitrijevic16@gmail.com</span>
        <span class="block mt-[10px]">Toronto, Ontario, Canada</span>
        
      </div>
    </div>
  </div>

</template>
<script>
// import HelloWorld from './components/HelloWorld.vue'
export default {
  data() {
    return {
      data: {},
      isPlaying: false,
      volume: 0.1,
      isMuted: true,
      workitems: [{
        'name': 'Making friends on video games',
        'video': '/src/assets/videos/lolvid.mp4',
        'isPlaying': false,
      },
      {
        'name': 'Asking AI to create an arm workout',
        'video': '/src/assets/videos/vid2.mp4',
        'isPlaying': false,
      },
      {
        'name': 'Consistency is key',
        'video': '/src/assets/videos/vid3.mp4',
        'isPlaying': false,
      },
      ]

    }
  },
  created() {

  },
  methods: {
    handleMouseLeave(event, item) {
      setTimeout(() => {
        event.target.pause();
      }, 500); // 500ms = 0.5 seconds
    },
    toggleMute() {
      const video = this.$refs.showcaseVideo;
      this.isMuted = !this.isMuted;
      video.muted = this.isMuted;

    },
    updateVolume() {
      const video = this.$refs.showcaseVideo;
      video.volume = this.volume;
      this.isMuted = this.volume == 0;
    }
  },
  mounted() {
    // Set initial volume
    const video = this.$refs.showcaseVideo;
    video.volume = this.volume;
  }
}
</script>
