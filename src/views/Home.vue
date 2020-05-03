<template>
  <div class="columns is-mobile is-centered">
    <div class="column is-half quiz-box">
      <div>
        <h3>1. Quran me total kitne Surahs hain? </h3>
      </div>
      <div>
        <ul>
          <li><h3>114</h3></li>

          <li><h3>117</h3></li>

          <li><h3>112</h3></li>

          <li><h3>115</h3></li>
        </ul>
      </div>
    </div>

  </div>
</template>

<script>

export default {
  name: 'Home',
  components: {
    
  }
}
</script>
<style scoped >
.quiz-box{
    background: #060814;
    height: 700px;
    width: 500px;
    border-radius: 20px;
    color: #fff;
    padding: 30px;
    font-family: 'Work Sans', sans-serif;
}
h3{
  font-size: 40px
}
li{
  border: 2px solid #4B5F9E ;
  margin-top: 10px;
  margin-bottom: 10px;
  border-radius: 20px;
  padding: 10px;
}
</style>