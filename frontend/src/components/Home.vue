<template>
  <div class="home">
    <h1>Welcome to {{ appName }}</h1>
    <video autoplay="true" id="videoElement">

    </video>
  </div>
</template>

<script>
  export default {
    name: 'Home',
    data: function() {
      return {
        appName: "Streamii"
      }
    },
    mounted () {
      navigator.mediaDevices.getUserMedia({ video: true, audio: true })
          .then(mediaStream => {
            this.$refs.video.srcObject = mediaStream
            this.$refs.video.play()
          })
          .catch(error => console.error('getUserMedia() error:', error))
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  h3 {
    margin: 40px 0 0;
  }
  ul {
    list-style-type: none;
    padding: 0;
  }
  li {
    display: inline-block;
    margin: 0 10px;
  }
  a {
    color: #42b983;
  }
</style>
