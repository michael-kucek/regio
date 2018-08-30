<template>
  <div>
    <h2>Cash</h2>
    <div class="cash-container">
      <div class="cash-denomination">
        <div>$100s</div>
        <input type="tel" v-model="hundreds" />
        <p>${{hundreds * 100}}</p>
      </div>
      <div class="cash-denomination">
        <div>$50s</div>
        <input type="tel" v-model="fifties" />
        <p>${{fifties * 50}}</p>
      </div>
      <div class="cash-denomination">
        <div>$20s</div>
        <input type="tel" v-model="twenties" />
        <p>${{twenties * 20}}</p>
      </div>
      <div class="cash-denomination">
        <div>$10s</div>
        <input type="tel" v-model="tens" />
        <p>${{tens * 10}}</p>
      </div>
      <div class="cash-denomination">
        <div>$5s</div>
        <input type="tel" v-model="fives" />
        <p>${{fives * 5}}</p>
      </div>
      <div class="cash-denomination">
        <div>$1s</div>
        <input type="tel" v-model="ones" />
        <p>${{ones}}</p>
      </div>
      <div class="cash-denomination">
        <div>¢25s</div>
        <input type="tel" v-model="quarters" />
        <p>${{quarters === 0 ? 0 : (quarters * 0.25).toFixed(2)}}</p>
      </div>
      <div class="cash-denomination">
        <div>¢10s</div>
        <input type="tel" v-model="dimes" />
        <p>${{dimes === 0 ? 0 : (dimes * 0.1).toFixed(2)}}</p>
      </div>
      <div class="cash-denomination">
        <div>¢5s</div>
        <input type="tel" v-model="nickels" />
        <p>${{nickels === 0 ? 0 : (nickels * 0.05).toFixed(2)}}</p>
      </div>
      <div class="cash-denomination">
        <div>¢1s</div>
        <input type="tel" v-model="pennies" />
        <p>${{pennies === 0 ? 0 : (pennies * 0.01).toFixed(2)}}</p>
      </div>
    </div>
    <h4>
      Cash Total: ${{total()}}
    </h4>
  </div>
</template>

<script>
export default {
  data() {
    return {
      hundreds: null,
      fifties: null,
      twenties: null,
      tens: null,
      fives: null,
      ones: null,
      quarters: null,
      dimes: null,
      nickels: null,
      pennies: null,
    };
  },
  methods: {
    total() {
      return (
        (this.hundreds * 100) + (this.fifties * 50) +
      (this.twenties * 20) + (this.tens * 1) +
      (this.fives * 5) + (this.ones * 1) +
      (this.quarters * 0.25) + (this.dimes * 0.10) +
       (this.nickels * 0.05) + (this.pennies * 0.01)).toFixed(2);
    },
  },
};
</script>
<style>
input {
  padding: 0.5em;
  width: 30%;
  font-size: 16px;
  background: #edfafa;
  border: none;
}
.cash-container {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
}
.cash-denomination {
  display: block;
  width: 30%;
  justify-content: space-between;
  /* border: 4px solid #2c3e50;
  border-radius: 3px; */
  padding: 0.5em;
  margin: 0.5em;
}
.cash-denomination > div {
  font-size: 1.2em;
}
.cash-denomination > p {
  color: cadetblue;
  font-weight: bold;
}
</style>
