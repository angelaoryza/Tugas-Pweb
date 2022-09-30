<script >
export default {
  data() {
    return {
      jam : 0,
      menit : 0,
      period : "AM"
    }
  },
  // name : 'DigiAlarm',
  // props : ' ',
  methods : {
      handlePlusJam () {
        this.jam += 1;
        if(this.jam > 23) {
            this.jam -= 24;
        }
      },
     handleMinJam () {
        this.jam -= 1;
        if(this.jam < 0) {
            this.jam = 0;
        }
      },
      handlePlusMenit () {
        this.menit += 1;
        if(this.menit > 59) {
            this.menit -= 60;
        }
      },
      handleMinMenit () {
        this.menit -= 1;
        if(this.menit < 0) {
            this.menit = 0;
        }
      },
  }
}
</script>

<template>
<div class="bg-gradient-to-r from-neutral-500 to-zinc-800 pt-0.5 w-3/4 mx-auto rounded-full shadow-lg shadow-indigo-500/40">
  <div class="p-3 relative mt-5 mx-auto bg-black w-3/5 justify-center shadow-lg shadow-black/50 rounded-lg">
    <span class="text-transparent text-4xl ml-1 mr-10 mt-10 bg-clip-text bg-gradient-to-r to-blue-500 from-pink-500" v-if="jam<10"> 0{{jam}}  </span>
    <span class="text-transparent text-4xl ml-1 mr-10 mt-10 bg-clip-text bg-gradient-to-r to-blue-500 from-pink-500" v-else-if="jam>=10"> {{jam}} </span>

    <span class="text-transparent text-4xl -ml-6 mr-48 my-2 bg-clip-text bg-gradient-to-r to-blue-500 from-pink-500"> : </span>

    <span class="text-transparent text-4xl -ml-44 mr-2 bg-clip-text bg-gradient-to-r to-blue-500 from-pink-500" v-if="menit<10"> 0{{menit}}  </span>
    <span class="text-transparent text-4xl -ml-44 mr-2 bg-clip-text bg-gradient-to-r to-blue-500 from-pink-500" v-else-if="menit>=10"> {{menit}}  </span>
  </div>

    <button class= "p-0.5 mb-5 mt-2 text-sm font-medium text-gray-900 rounded-full group bg-gradient-to-br from-cyan-500 to-blue-500 group-hover:from-cyan-500 group-hover:to-blue-500 hover:text-white dark:text-white focus:ring-4 focus:outline-none focus:ring-cyan-200 dark:focus:ring-cyan-800" @click="handlePlusJam">
     <span class="relative px-1.5 transition-all ease-in duration-75 bg-white dark:bg-gray-900 rounded-full group-hover:bg-opacity-0"> +  </span>
    </button>
    <button class= "relative inline-flex items-center justify-center p-0.5 mb-2 mr-19 ml-2 overflow-hidden text-sm text-gray-900 rounded-full group bg-gradient-to-br from-pink-500 to-orange-400 group-hover:from-pink-500 group-hover:to-orange-400 hover:text-white dark:text-white focus:ring-4 focus:outline-none focus:ring-pink-200 dark:focus:ring-pink-800" @click="handleMinJam"> 
      <span class="relative px-2 transition-all ease-in duration-75 bg-white dark:bg-gray-900 rounded-full group-hover:bg-opacity-0"> - </span>
    </button>

    <button class="relative inline-flex items-center justify-center p-0.5 ml-8 mb-2 -mr-2 overflow-hidden text-sm font-medium text-gray-900 rounded-full group bg-gradient-to-br from-cyan-500 to-blue-500 group-hover:from-cyan-500 group-hover:to-blue-500 hover:text-white dark:text-white focus:ring-4 focus:outline-none focus:ring-cyan-200 dark:focus:ring-cyan-800" @click="handlePlusMenit"> 
      <span class="relative px-1.5  transition-all ease-in duration-75 bg-white dark:bg-gray-900 rounded-full group-hover:bg-opacity-0 "> + </span>
    </button>
    <button class="relative inline-flex items-center justify-center p-0.5 ml-4 mb-2 mr-2 overflow-hidden text-sm font-medium text-gray-900 rounded-full group bg-gradient-to-br from-pink-500 to-orange-400 group-hover:from-pink-500 group-hover:to-orange-400 hover:text-white dark:text-white focus:ring-4 focus:outline-none focus:ring-pink-200 dark:focus:ring-pink-800" @click="handleMinMenit"> 
      <span class="relative px-2 transition-all ease-in duration-75 bg-white dark:bg-gray-900 rounded-full group-hover:bg-opacity-0"> - </span>
    </button>
    <br>
</div>
</template>

