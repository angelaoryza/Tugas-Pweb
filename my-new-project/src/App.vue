
<script>
import DigiAlarm from './components/DigiAlarm.vue'
import SWU from './assets/Stuck-With-U.mp3'
export default {
  data() {
    return {
      waktu : "00:00:00",
      alarm : "00:00:00",
      timer : 0,
      text : ""
    }
  },
  methods: {
      sesuaiinAlarm () {
      var jam = this.$refs.alarm.jam;
      var menit = this.$refs.alarm.menit;
      var periode = this.$refs.alarm.periode;
      if(jam > 12) {
        jam -= 12;
        periode = "PM";
      }

      if(jam < 12) {
        periode = "AM";
      }

      jam = jam < 10 ? "0" + jam : jam;
      menit = menit < 10 ? "0" + menit : menit;

      let alarm = jam + ":" + menit + ":" + "00" + " " + periode;
      return alarm;
    },
    displayTime() {
        const timeNow = new Date();

        let hourOfDay = timeNow.getHours();

        let minutes = timeNow.getMinutes();
        let seconds = timeNow.getSeconds();
        let period = "AM";

        if(hourOfDay > 12) {
            hourOfDay -= 12;
            period = "PM";
            }

            if(hourOfDay == 0) {
            hourOfDay = 12;
            period = "AM";
            }

        hourOfDay = hourOfDay < 10 ? "0" + hourOfDay : hourOfDay;
        minutes = minutes < 10 ? "0" + minutes : minutes;
        seconds = seconds < 10 ? "0" + seconds : seconds;

        let time = hourOfDay + ":" + minutes + ":" + seconds + " " + period;
        return time;
    }
  },

  components: {
      DigiAlarm
  },

  mounted: function() {
    this.timer = setInterval(()=> {
      this.waktu = this.displayTime();
      this.alarm = this.sesuaiinAlarm();
      if (this.waktu === this.alarm) {
        var audio = new Audio(SWU);
        audio.play();
        var berisik = setInterval(function(){
          if(audio.currentTime > 10){
            if(confirm("Wake Up! Do you want to turn off the alarm?")) {
              audio.pause();
              clearInterval(berisik);
            }
            else {
              audio.play();
            }
        }
        },1000);
      }
    },1000)

  //     let person = prompt("Please enter your name:", "Harry Potter");
  // if (person == null || person == "") {
  //   this.text = "User cancelled the prompt.";
  // } else {
  //   this.text = person;
  // }
  },

  beforeUnmount() {
    clearInterval(this.timer)
  }
}
</script>

<template>
<div class="relative w-3/4 mx-auto">
  <div>
    <span class="text-8xl"> Hello </span>
    <img class="inline w-1/5 mx-5" src="./assets/bunny.png">
    <span class="text-8xl"> {{text}} </span>
  </div>
  <div class="border-4 border-x-red-500 border-y-blue-800/50 w-85 text-8xl text-white bg-black hover:bg-gradient-to-r to-blue-800 from-red-500 hover:border-x-slate-500 hover:border-y-slate-50 hover:text-white focus:ring-4 focus:ring-blue-300 font-medium rounded-xl text-sm px-5 py-2.5 mr-4 mb-5  focus:outline-none ">
    <span class="font-mono text-transparent text-8xl bg-clip-text bg-gradient-to-r to-blue-800 from-red-500 hover:text-white">{{waktu}}</span>
  </div> 
  <div>
  <DigiAlarm ref="alarm"> </DigiAlarm>
    <button class="text-white bg-gradient-to-r from-purple-500 via-purple-600 to-purple-700 hover:bg-gradient-to-br focus:ring-4 focus:outline-none focus:ring-purple-300 dark:focus:ring-purple-800 font-medium rounded-lg text-sm px-5 py-2.5 text-center mr-2 mb-2 mt-5" @click="sesuaiinAlarm"> SET ALARM </button>
  </div>
</div> 
</template>



