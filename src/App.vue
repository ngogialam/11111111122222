<template>
  <div id="app">
    <body>
      <div class="wrapper clearfix">
        <players
        v-bind:isWinner="isWinner"
          v-bind:scoresPlayer="scoresPlayer"
          v-bind:activePlayer="activePlayer"
          v-bind:currentScore="currentScore"
        />

        <controls
        
          v-bind:isPlaying="isPlaying"
          v-on:handleChangeFinalScore="handleChangeFinalScore"
          v-bind:finalScore="finalScore"
          v-on:handleRollDice="handleRollDice"
          v-on:handleNewGame="handleNewGame"
          v-on:handleHoldScore="handleHoldScore"
        />
        <dices v-bind:dices="deces" />
        <popup-rule
          v-bind:isOpenPopup="isOpenPopup"
          v-on:handleConfirm="handleConfirm"
        />
        <test001 />
        <database />
      </div>
    </body>
  </div>
</template>

<script>
import Players from "./components/Players.vue";
import Dices from "./components/Dices.vue";
import Test001 from "./components/Test001.vue";
import PopupRule from "./components/PopupRule.vue";
import Database from "./components/Database.vue";

import Controls from "./components/Controls.vue";
export default {
  name: "app",
  data() {
    return {
      isPlaying: false,
      isOpenPopup: false,
      activePlayer: 0, //nguoi choi hien tai
      scoresPlayer: [10, 20],
      currentScore: 30,
      dices: [5, 5],
      finalScore: 20
    };
  },
computed: {    
  
  




// isWinner() {
//   let { scoresPlayer, finalScore } = this;
//   if (scoresPlayer[0] >= finalScore || scoresPlayer[1] >= finalScore) {
//     // dung cuoc choi
//     this.isPlaying = false;
//     return true;
//   }
//   return false;
// }
  },
  components: {
    Players,
    Controls,
    Dices,
    Test001,
    PopupRule,
    Database,
  },
  methods: {
    handleChangeFinalScore(e) {
      // console.log(parseInt(e.target.value));
      var number = parseInt(e.target.value);
      if (isNaN(number)) {
        this.finalScore = "";
      } else {
        this.finalScore = number;
      }
    },
    handleHoldScore() {
      if (this.isPlaying) {
        // activePlayer = 0 -> Nguoi choi 1
        // activePlayer = 0 -> Nguoi choi 2
        // socresPlayer -> array
        // scorePlayer[0] = scorePlayer[activePlayer]
        // scorePlayer[1] = scorePlayer[activePlayer]
        //   this.scoresPlayer[this.activePlayer] = this.currentScore + this.scoresPlayer[this.activePlayer];
        let { scoresPlayer, activePlayer, currentScore } = this;
        let scoreOld = scoresPlayer[activePlayer];
        let cloneScorePlayer = [...scoresPlayer];
        cloneScorePlayer[activePlayer] = scoreOld + currentScore;
        // this.scoresPlayer[activePlayer] = scoreOld + currentScore;
        this.scoresPlayer = cloneScorePlayer; /// nhu ham o duoi
        // this.$set(this.scoresPlayer, activePlayer, scoreOld + currentScore);






        if (!this.isWinner) {
          this.nextPlayer();
        }
        // this.nextPlayer();
        console.log(this.cloneScorePlayer);

        // console.log("handleHoldScore App.vue");
      } else {
        alert("ban chua an nut New Game");
      }
    },
    nextPlayer() {
      this.activePlayer = this.activePlayer === 0 ? 1 : 0;
      this.currentScore = 0;
    },
    handleNewGame() {
      console.log("handleNewGame App.vue"); //show luat choi
      this.isOpenPopup = true;
    },
    handleConfirm() {
      // console.log('handleConfirm App.vue')
      this.isPlaying = true;
      this.isOpenPopup = false;
      this.activePlayer = 0;
      this.scoresPlayer = [0, 0];
      this.currentScore = 0;
      this.dices = [1, 1];
    },
    handleRollDice() {
      console.log("handelRollDice App.vue");
      // this.
      if (this.isPlaying) {
        // xoay xuc sac
        var dice1 = Math.floor(Math.random() * 6) + 1;
        var dice2 = Math.floor(Math.random() * 6) + 1;

        console.log(dice1, dice2);
        this.dices = [dice1, dice2]; /// k hiển thị giá trị của dice1,dice2 ??? loi []
        if (dice1 === 1 || dice2 === 1) {
          //     let activePlayer = this.activePlayer;
          //   setTimeout(function() {
          //       console.log(this);
          alert(
            "Người chơi Player ${this.activePlayer + 1} đã quay trúng số 1. Rất tiếc "
          );
          //   }, 10);
          // doi luot choi
          //reset diem tam thoi ve 0
          this.nextPlayer();
        } else {
          //cong don diem cho ng dang choi
          this.currentScore = this.currentScore + dice1 + dice2;
        }
      } else {
        alert("Vui lòng ấn vào nút New Game");
      }
    }
  }
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.clearfix::after {
  content: "";
  display: table;
  clear: both;
}

body {
  background-image: linear-gradient(
      rgba(62, 20, 20, 0.4),
      rgba(62, 20, 20, 0.4)
    ),
    url("./assets/back.jpg");
  background-size: cover;
  background-position: center;
  font-family: Lato;
  font-weight: 300;
  position: relative;
  height: 100vh;
  color: #555;
}

.wrapper {
  width: 1000px;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background-color: #fff;
  box-shadow: 0px 10px 50px rgba(0, 0, 0, 0.3);
  overflow: hidden;
}

/* diece lllllllllllllllllllllllllllllllllllllllllllll*/
#dice-1 {
  top: 120px;
}
#dice-2 {
  top: 250px;
}

.dice {
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
  width: 120px;
  height: 120px;
  box-shadow: 0px 10px 60px rgba(0, 0, 0, 0.1);
}
.spinner div {
  position: absolute;
  width: 120px;
  height: 120px;
  border: 1px solid #ccc;
  box-shadow: 0 0 20px rgba(0, 0, 0, 0.2);
  text-align: center;
  line-height: 120px;
  font-size: 100px;
  color: #42b983;
  font-size: 0;
  transition: all 0.3s ease;
  opacity: 1;
}

.spinner .face1 {
  -webkit-transform: translateZ(60px);
  -ms-transform: translateZ(60px);
  transform: translateZ(60px);
  background-image: url("./assets/dice-1.png");
  background-position: center;
  background-size: cover;
}
.spinner .face2 {
  -webkit-transform: rotateY(90deg) translateZ(60px);
  -ms-transform: rotateY(90deg) translateZ(60px);
  transform: rotateY(90deg) translateZ(60px);
  background-image: url("./assets/dice-2.png");
  background-position: center;
  background-size: cover;
}
.spinner .face3 {
  -webkit-transform: rotateY(90deg) rotateX(90deg) translateZ(60px);
  -ms-transform: rotateY(90deg) rotateX(90deg) translateZ(60px);
  transform: rotateY(90deg) rotateX(90deg) translateZ(60px);
  background-image: url("./assets/dice-3.png");
  background-position: center;
  background-size: cover;
}
.spinner .face4 {
  -webkit-transform: rotateY(180deg) rotateZ(90deg) translateZ(60px);
  -ms-transform: rotateY(180deg) rotateZ(90deg) translateZ(60px);
  transform: rotateY(180deg) rotateZ(90deg) translateZ(60px);
  background-image: url("./assets/dice-4.png");
  background-position: center;
  background-size: cover;
}
.spinner .face5 {
  -webkit-transform: rotateY(-90deg) rotateZ(90deg) translateZ(60px);
  -ms-transform: rotateY(-90deg) rotateZ(90deg) translateZ(60px);
  transform: rotateY(-90deg) rotateZ(90deg) translateZ(60px);
  background-image: url("./assets/dice-5.png");
  background-position: center;
  background-size: cover;
}
.spinner .face6 {
  -webkit-transform: rotateX(-90deg) translateZ(60px);
  -ms-transform: rotateX(-90deg) translateZ(60px);
  transform: rotateX(-90deg) translateZ(60px);
  background-image: url("./assets/dice-6.png");
  background-position: center;
  background-size: cover;
}
</style>

