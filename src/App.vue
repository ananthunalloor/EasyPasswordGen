<script>
export default {
  data() {
    return {
      passLength: "8",
      genPass: "generate a long password",
    };
  },
  methods: {
    genPassword() {
      this.genPass = "";
      var chars =
        "0123456789abcdefghijklmnopqrstuvwxyz!@#$%^&*()ABCDEFGHIJKLMNOPQRSTUVWXYZ";
      var passwordLength = this.passLength;
      var password = "";
      for (var i = 1; i <= passwordLength; i++) {
        var randomNumber = Math.floor(Math.random() * chars.length);
        password += chars.substring(randomNumber, randomNumber + 1);
      }
      this.genPass = password;
    },
    copyPass()
    {
      const cb = navigator.clipboard;
      cb.writeText(this.genPass);
    }
  },
};
</script>

<template>
  <div class="mainBody">
    <div class="mainContent">
      <div class="passField">
        <span class="genPass">{{ genPass }}</span>
        <div class="copyIcon" @click="copyPass()"></div>
      </div>
      <select v-model="passLength">
        <option value="8">8</option>
        <option value="9">9</option>
        <option value="10">10</option>
        <option value="11">11</option>
        <option value="12">12</option>
        <option value="13">13</option>
        <option value="14">14</option>
        <option value="15">15</option>
        <option value="16">16</option>
        <option value="17">17</option>
        <option value="18">18</option>
        <option value="19">19</option>
        <option value="20">20</option>
      </select>
      <button class="genBtn" @click="genPassword()">GENERATE</button>
    </div>
  </div>
</template>

<style>
* {
  margin: 0;
  padding: 0;
}
body {
  width: 500px;
  height: 75px;
  font-family: "Nunito";
}
#app {
  width: 100%;
  height: 100%;
  background-color: #f3f5f7;
}
.mainBody {
  padding: 15px;
}
.mainContent {
  display: flex;
  justify-content: space-between;
}
.genPass {
  padding: 10px 20px;
  display: inline-block;
  font-size: 13px;
  font-style: italic;
  font-weight: 200;
  line-height: 18px;
}
.copyIcon {
  width: 20px;
  height: 20px;
  padding: 5px;
  margin: 4px 10px;
  border-radius: 5px;
  background-image: url("/icon.svg");
  background-repeat: no-repeat;
  background-size: 25px;
  background-position: center;
  display: inline-block;
}
.copyIcon:hover {
  background-color: #474747;
}
.genBtn {
  width: 90px;
  height: 40px;
  border-radius: 8px;
  background: #d3d3d3;
  border: none;
  font-size: 12px;
  font-weight: 400;
}
.passField {
  width: 320px;
  height: 40px;
  border-radius: 20px;
  background-color: #121e2c;
  color: #F3F5F7;
  display: flex;
  justify-content: space-between;
}
select {
  width: 50px;
  height: 40px;
  color: #121e2c;
  background-color: #d3d3d3;
  border: none;
  border-radius: 8px;
  font-size: 15px;
  font-weight: 500;
  padding-left: 8px;
}
option {
  font-size: 14px;
  font-weight: 500;
  border-radius: 8px;
  padding-left: 10px;
}
</style>
