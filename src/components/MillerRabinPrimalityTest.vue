<template>
  <div>
    <h1>Miller Rabin Primality Test Online</h1>
    <p>
      The Miller–Rabin primality test or Rabin–Miller primality test is a primality test.
      <br> An algorithm which determines whether a given number is prime
    </p>
    <h3>Input Your Big Integer</h3>
    <p>
      <small><a href="https://primes.utm.edu/lists/small/small3.html" title="List of prime numbers" target="_blank">Get List of prime numbers ➢</a></small>
    </p>
    <br>
    <textarea @keydown="resetResult" v-model="bigNumber" placeholder="Enter your number"></textarea>

    <p>
      <span v-if="error" class="error">{{error}}</span>
      <span v-if="bigNumber.length && isPrimeNumber != null">
        Number is
        <span v-if="!isPrimeNumber">not prime</span>
        <strong v-if="isPrimeNumber">Prime</strong>
      </span>
    </p>

    <p>
       <button v-on:click="checkPrime" class="btn btn-sm btn-primary text-white" type="button">Check</button>
    </p>

    <footer>
      <h3>Credits</h3>
      <ul>
        <li><a href="https://github.com/peterolson/BigInteger.js" target="_blank" rel="noopener">BigInteger.js</a></li>
      </ul>
      <h3>First 1000 digits prime number in Pi</h3>
      <pre>
        3345477624168625189835694855620992192221842725502542568876717904946016534668049886272327917860857843838279679766814541009538837863609506800642251252051173929848960841284886269456042419652850222106611863067442786220391949450471237137869609563643719172874677646575739624138908658326459958133904780275900994657640789512694683983525957098258226205224894077267194782684826014769909026401363944374553050682034962524517493996514314298091906592509372216964615157098583874105978859597729754989301617539284681382686838689427741559918559252459539594310499725246808459872736446958486538367362226260991246080512438843904512441365497627807977156914359977001296160894416948685558484063534220722258284886481584560285060168427394522674676788952521385225499546667278239864565961163548862305774564980355936345681743241125150760694794510965960940252288797108931456691368672287489405601015033086179286809208747609178249385890097149096759852613655497818931297848216829989487226588048575640142704775551323796414515237462343
      </pre>
    </footer>
  </div>
</template>

<script>
var bigInt = require("big-integer");
export default {
  name: 'MillerRabinPrimalityTest',
  props: {
  },
  data() {
    return {
      error: null,
      isPrimeNumber: null,
      bigNumber: ''
    }
  },
  methods: {
    resetResult: function() {
      this.isPrimeNumber = null
      this.error = null
    },
    checkPrime: function() {
      try {
        this.bigNumber = this.bigNumber.trim()
        this.isPrimeNumber = bigInt(this.bigNumber).isProbablePrime()
      } catch(e) {
        this.isPrimeNumber = null
        this.error = e
      }
    }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
pre{
  margin:30px;
  overflow-x: auto;
  white-space: pre-wrap;
  white-space: -moz-pre-wrap;
  white-space: -pre-wrap;
  white-space: -o-pre-wrap;
  word-wrap: break-word;
}
footer {
  margin-top:200px;
}
@media all{
.btn{-moz-appearance:none;-moz-user-select:none;-ms-user-select:none;-webkit-appearance:none;-webkit-user-select:none;appearance:none;background-position:-1px -1px;background-repeat:repeat-x;background-size:110% 110%;border:1px solid rgba(27,31,35,.2);border-radius:.25em;cursor:pointer;display:inline-block;font-size:14px;font-weight:600;line-height:20px;padding:6px 12px;position:relative;user-select:none;vertical-align:middle;white-space:nowrap;}
.btn:hover{background-repeat:repeat-x;text-decoration:none;}
.btn:focus{outline:0;}
.btn:disabled{background-position:0 0;cursor:default;}
.btn:active{background-image:none;}
.btn{background-color:#eff3f6;background-image:linear-gradient(-180deg,#fafbfc,#eff3f6 90%);color:#24292e;}
.btn:focus{box-shadow:0 0 0 .2em rgba(3,102,214,.3);}
.btn:hover{background-color:#e6ebf1;background-image:linear-gradient(-180deg,#f0f3f6,#e6ebf1 90%);background-position:-.5em;border-color:rgba(27,31,35,.35);}
.btn:active{background-color:#e9ecef;background-image:none;border-color:rgba(27,31,35,.35);box-shadow:inset 0 .15em .3em rgba(27,31,35,.15);}
.btn:disabled{background-color:#eff3f6;background-image:none;border-color:rgba(27,31,35,.2);box-shadow:none;color:rgba(36,41,46,.4);}
.btn-primary{background-color:#28a745;background-image:linear-gradient(-180deg,#34d058,#28a745 90%);color:#fff;}
.btn-primary:focus{box-shadow:0 0 0 .2em rgba(52,208,88,.4);}
.btn-primary:hover{background-color:#269f42;background-image:linear-gradient(-180deg,#2fcb53,#269f42 90%);background-position:-.5em;border-color:rgba(27,31,35,.5);}
.btn-primary:active{background-color:#279f43;background-image:none;border-color:rgba(27,31,35,.5);box-shadow:inset 0 .15em .3em rgba(27,31,35,.15);}
.btn-primary:disabled{background-color:#94d3a2;background-image:none;border-color:rgba(27,31,35,.2);box-shadow:none;color:hsla(0,0%,100%,.75);}
.btn-sm{font-size:12px;line-height:20px;padding:3px 10px;}
:-ms-input-placeholder{color:#6a737d;}
::-ms-input-placeholder{color:#6a737d;}
::placeholder{color:#6a737d;}
.text-white{color:#fff!important;}
}
@media all{
@media print{
.btn:not(.btn-outline){background:none;color:#24292e!important;}
}
}
h3 {
  margin-top: 40px;
  margin-bottom: -5px;
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
.error {
  color: red;
}
textarea:active, textarea:focus, textarea:hover{
  outline:0px !important;
  -webkit-appearance:none;
  border: 3px solid #bab6b6;
}
textarea {
  padding:10px;
  border: 3px solid lightgray;
  border-radius: 4px;
  min-height: 150px;
  min-width: 300px;
}
</style>
