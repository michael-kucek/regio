<template>
  <div v-on:keydown="pause($event)" class="holder">
    <h2>cards</h2>
    <money v-model="price" v-bind="money" ref="moneybox"></money>
    <div class="timer" v-bind:class="{ isTyping: isTyping}" />
    <div class="card-container">
      <div class="card-list" v-for="(transaction, index) in transactions" :key="transaction.card">
        <h4 v-bind:class="{ active: cardType ===  index}" v-on:click="changeCardType(index)">
          {{transaction.card}}
        </h4>
        <div class="total">
          {{transaction.charges.reduce((p, c) => p + c.amount, 0).toFixed(2)}}
        </div>
        <div v-for="charge in transaction.charges" :key="charge.time">
          <div class="charge-amount" v-on:click="deleteCharge(index, charge.time)">
            {{ charge.amount.toFixed(2) }}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { Money } from 'v-money';

export default {
  components: { Money },
  data() {
    return {
      price: 0,
      isTyping: false,
      transactions: [
        { card: 'visa', charges: [] },
        { card: 'mc', charges: [] },
        { card: 'amex', charges: [] },
        { card: 'other', charges: [] },
      ],
      time: null,
      money: {
        decimal: '.',
        thousands: ',',
        prefix: '$ ',
        suffix: '',
        precision: 2,
        masked: false,
      },
      cardType: 0,
    };
  },
  methods: {
    pause(event) {
      if (event.key === 'v' || event.key === 'V') {
        this.cardType = 0;
      }
      if (event.key === 'm' || event.key === 'M') {
        this.cardType = 1;
      }
      if (event.key === 'd' || event.key === 'D') {
        this.cardType = 2;
      }
      if (event.key === 'o' || event.key === 'O') {
        this.cardType = 3;
      }
      clearTimeout(this.time);
      if (this.price === 0) return;
      this.isTyping = true;
      this.time = setTimeout(() => {
        this.transactions[this.cardType].charges.push({
          time: new Date().toString(),
          amount: this.price,
          dollars: Math.floor(this.price),
          cents: Math.floor((this.price - Math.floor(this.price)) * 100),
        });
        this.price = 0;
        this.isTyping = false;
      }, 1000);
    },
    changeCardType(i) {
      this.cardType = i;
      this.$refs.moneybox.$el.focus();
    },
    deleteCharge(cardType, key) {
      this.transactions[cardType].charges =
      this.transactions[cardType].charges
        .filter(t => t.time !== key);
    },
  },
};
</script>

<style scoped>
input {
  padding: 0.5em;
  width: 60%;
  font-size: 25px;
  background: #edfafa;
  border: none;
}
.card-container {
  display: flex;
  justify-content: space-around;
  flex-wrap: nowrap;
  font-size: 1.2em;
}
.card-container > div {
  font-family: "Lucida Console";
  text-align: right;
}
.total {
  margin-bottom: 1em;
  color: cadetblue;
  font-weight: bold;
}
.active {
  text-decoration: underline;
  color: #00acc1;
}

.charge-amount:hover {
  text-decoration: line-through;
  color: #a04b70;
}
.timer {
  display: none;
  height: 8px !important;
  width: 4%;
  margin: auto;
  background-color: red;
  content: "";
  padding: 0em 0.5em;
  font-size: 25px;
}
.isTyping {
  animation: bounce 2s linear 0s infinite;
}
@keyframes bounce {
  0% {
    transform: translateX(0);
  }
  25% {
    transform: translateX(-100%);
  }
  50% {
    transform: translateX(0);
  }
  75% {
    transform: translateX(100%);
  }
  100% {
    transform: translateX(0);
  }
}
</style>
