<template>
  <main>
    <h1>Generate A Random Password</h1>
    <form action="">
      <label for="length">Choose The Password Length</label>
      <input type="number" id="length" v-model="length" min="0" max="50" />
      <button type="submit" id="gen" @click.prevent="genpass">Generate</button>
      <div class="res">
        <div class="action">
          <small @click="copyText">Copy</small>
          <i class="fa fa-copy" @click="copyText"></i>
        </div>
        <p id="res"></p>
      </div>
      <label for="res"></label>
      <button type="button" @click="reset">Generate Another</button>
    </form>
  </main>
</template>

<script>
export default {
  name: "PassGen",
  data() {
    return {
      randomChars:
        "abcdefghijklmnopqrstuvwxyz0123456789!@#$%^&*()ABCDERFGIJKLMNOPQRSTUVWXYZ",
      length: length,
    };
  },
  methods: {
    genpass() {
      if (this.length <= 50 && this.length > 0) {
        this.reset();
        for (let i = 0; i < this.length; i++) {
          let pass = Math.floor(Math.random() * this.randomChars.length);
          document.getElementById("res").textContent += this.randomChars[pass];
        }
        document.querySelector("main form .res .action").style.visibility =
          "visible";
      } else if (this.length > 50) {
        document.getElementById("res").textContent =
          "Max Password Charachters Is 50";
        document.getElementById("res").style.color = "red";
        document.querySelector("main form .res").style.outlineColor = "red";
        document.querySelector("main form .res .action").style.visibility =
          "hidden";
      } else if (this.length === 0) {
        document.getElementById("res").textContent =
          "Password Length Can Not Be 0";
        document.getElementById("res").style.color = "red";
        document.querySelector("main form .res").style.outlineColor = "red";
        document.querySelector("main form .res .action").style.visibility =
          "hidden";
      } else if (this.length < 0) {
        document.getElementById("res").textContent =
          "Password Length Can Not Be Negative";
        document.getElementById("res").style.color = "red";
        document.querySelector("main form .res").style.outlineColor = "red";
        document.querySelector("main form .res .action").style.visibility =
          "hidden";
      }
    },
    copyText() {
      if (document.getElementById("res").textContent) {
        navigator.clipboard.writeText(
          document.getElementById("res").textContent
        );
        document.querySelector("main form .action small").textContent =
          "Copied";
        document.querySelector("main form .action i").className = "fa fa-check";
        document.querySelector("main form .action").style.backgroundColor =
          "#00";

        setTimeout(() => {
          document.querySelector("main form .action small").textContent =
            "Copy";
          document.querySelector("main form .action i").className =
            "fa fa-copy";
        }, 5000);
      }
    },
    reset() {
      document.getElementById("res").textContent = "";
      document.querySelector("main form .res").style.outlineColor = "#3f51b5";
      document.querySelector("main form .res .action").style.visibility =
        "hidden";
      document.querySelector("main form .res p").style.color = "black";
      document.getElementById("length").value = 0;
    },
  },
};
</script>

<style>
* {
  box-sizing: border-box;
}

main > * {
  z-index: 2;
}

h1 {
  color: white;
  text-align: center;
}
main {
  z-index: 1;
  overflow: hidden;
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
  box-shadow: rgba(0, 0, 0, 0.56) 0px 22px 70px 4px;
  padding: 60px 30px;
  border-radius: 20px;
  width: 723.38px;
  max-width: 100%;
  background: #99282852;
  backdrop-filter: blur(10px);
}
form {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 20px;
  padding: 20px 40px;
  font-size: 19px;
}

form label {
  color: white;
  width: 100%;
}

form input {
  padding: 20px 10px;
  font-size: 23px;
  outline: 1px solid #3f51b5;
  grid-column: 1/2;
}

form .res {
  background-color: white;
  grid-column: 1/3;
  cursor: none;
  height: 68px;
  padding: 20px 10px;
  font-size: 23px;
  outline: 1px solid #3f51b5;
  display: flex;
  align-items: center;
  cursor: default;
  overflow-x: scroll;
  overflow-y: hidden;
  position: relative;
}

form .res::-webkit-scrollbar {
  display: none;
}

form .res .action {
  display: flex;
  align-items: center;
  gap: 5px;
  cursor: pointer;
  position: fixed;
  left: 80%;
  font-size: 13px;
  color: white;
  background-color: #000;
  padding: 5px;
  border-radius: 5px;
  visibility: hidden;
}

form .res > * {
  margin: 0;
}

form button {
  padding: 20px 30px;
  color: #fff;
  border: none;
  background: #000;
  font-size: 23px;
  transition: 0.3s;
  cursor: pointer;
  text-transform: uppercase;
  letter-spacing: 2px;
}

form button:last-of-type {
  grid-column: 1/3;
}

form button:hover {
  background-color: #3f51b5;
}
</style>
