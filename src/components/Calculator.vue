<template>
  <div class="p-3" style="width: 414px; height: 896px">
    <p id="answer" class="text-end mb-0 me-3 text-truncate">{{ans}}</p>
    <div class="d-flex gap-3 justify-content-center mb-3">
      <button @click="clearAll()" v-if='x == "" || y == ""' class="circ btn bg-grey text-black rounded-circle d-flex">
        <p class="text-center m-auto p-0" style="font-weight: 500">AC</p>
      </button>
      <button @click="clearAns()" v-else class="circ btn bg-grey text-black rounded-circle d-flex">
        <p class="text-center m-auto p-0" style="font-weight: 500">C</p>
      </button>
      <button @click="toggleNegative()" class="circ btn bg-grey text-black rounded-circle d-flex">
        <p class="text-center m-auto p-0"><i class="bi bi-plus-slash-minus"></i></p>
      </button>
      <button @click="setPercentage()" class="circ btn bg-grey text-black rounded-circle d-flex">
        <p class="text-center m-auto p-0"><i class="bi bi-percent"></i></p>
      </button>
      <button id="divide" @click="setNumber('/')" class="circ btn btn-warning text-white rounded-circle d-flex">
        <p class="text-center m-auto p-0"><i class="fa-solid fa-divide"></i></p>
      </button>
    </div>
    <div class="d-flex gap-3 justify-content-center mb-3">
      <button class="circ btn bg-darkgrey text-white rounded-circle d-flex">
        <p @click="setNumber(7)" class="text-center m-auto p-0" style="font-weight: 500">7</p>
      </button>
      <button @click="setNumber(8)" class="circ btn bg-darkgrey text-white rounded-circle d-flex">
        <p class="text-center m-auto p-0" style="font-weight: 500">8</p>
      </button>
      <button @click="setNumber(9)" class="circ btn bg-darkgrey text-white rounded-circle d-flex">
        <p class="text-center m-auto p-0" style="font-weight: 500">9</p>
      </button>
      <button id="multiply" @click="setNumber('*')" class="circ btn btn-warning text-white rounded-circle d-flex">
        <p class="text-center m-auto p-0"><i class="fa-solid fa-xmark"></i></p>
      </button>
    </div>
    <div class="d-flex gap-3 justify-content-center mb-3">
      <button @click="setNumber(4)" class="circ btn bg-darkgrey text-white rounded-circle d-flex">
        <p class="text-center m-auto p-0" style="font-weight: 500">4</p>
      </button>
      <button @click="setNumber(5)" class="circ btn bg-darkgrey text-white rounded-circle d-flex">
        <p class="text-center m-auto p-0" style="font-weight: 500">5</p>
      </button>
      <button @click="setNumber(6)" class="circ btn bg-darkgrey text-white rounded-circle d-flex">
        <p class="text-center m-auto p-0" style="font-weight: 500">6</p>
      </button>
      <button id="minus" @click="setNumber('-')" class="circ btn btn-warning text-white rounded-circle d-flex">
        <p class="text-center m-auto p-0"><i class="fa-solid fa-minus"></i></p>
      </button>
    </div>
    <div class="d-flex gap-3 justify-content-center mb-3">
      <button @click="setNumber(1)" class="circ btn bg-darkgrey text-white rounded-circle d-flex">
        <p class="text-center m-auto p-0" style="font-weight: 500">1</p>
      </button>
      <button @click="setNumber(2)" class="circ btn bg-darkgrey text-white rounded-circle d-flex">
        <p class="text-center m-auto p-0" style="font-weight: 500">2</p>
      </button>
      <button @click="setNumber(3)" class="circ btn bg-darkgrey text-white rounded-circle d-flex">
        <p class="text-center m-auto p-0" style="font-weight: 500">3</p>
      </button>
      <button id="plus" @click="setNumber('+')" class="circ btn btn-warning text-white rounded-circle d-flex">
        <p class="text-center m-auto p-0"><i class="fa-solid fa-plus"></i></p>
      </button>
    </div>
    <div class="d-flex gap-3 justify-content-center mb-3">
      <button @click="setNumber(0)" class="long btn bg-darkgrey text-white rounded-pill d-flex">
        <p class="text-start ms-3 my-auto p-0" style="font-weight: 500">0</p>
      </button>
      <button @click="setNumber('.')" class="circ btn bg-darkgrey text-white rounded-circle d-flex">
        <p class="text-center m-auto p-0" style="font-weight: 500">.</p>
      </button>
      <button @click="math()" class="circ btn btn-warning text-white rounded-circle d-flex">
        <p class="text-center m-auto p-0"><i class="fa-solid fa-equals"></i></p>
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CalculatorApp',
  data() {
    return {
      ans: '0',
      prev: '',
      x: '',
      y: '',
      isOperator: false,
    }
  },
  methods: {
    async math() {
      let query = ''
      query = this.x + this.y
      console.log('query', query)

      let encoded = encodeURIComponent(query)
      const response = await fetch(`http://api.mathjs.org/v4/?expr=${encoded}`)
      const data = await response.json()
      this.ans = String(data)
      this.y = String(data)
      this.x = ''
      this.resetButtons()
    },

    setNumber(num) {
      if (typeof num == 'string' && num != '.') {
        this.operatorCount++
        this.isOperator = true

        this.resetButtons()
        this.setButtonStyle(num)

        this.x = this.y
        this.prev = this.y
        this.y = ''
        this.x = this.x + String(num)
      } else {
        if (this.isOperator) {
          this.ans = String(num)
          this.isOperator = false
        } else {
          if (this.ans == '0' && num != '.')
            this.ans = String(num)
          else
            this.ans = this.ans + String(num)
        }
        this.y = this.y + String(num)
      }
    },

    setButtonStyle(num) {
      if (num == '+') {
        document.getElementById('plus').classList.remove('text-white')
        document.getElementById('plus').classList.add('bg-white')
        document.getElementById('plus').classList.add('text-warning')
      }

      if (num == '-') {
        document.getElementById('minus').classList.remove('text-white')
        document.getElementById('minus').classList.add('bg-white')
        document.getElementById('minus').classList.add('text-warning')
      }

      if (num == '*') {
        document.getElementById('multiply').classList.remove('text-white')
        document.getElementById('multiply').classList.add('bg-white')
        document.getElementById('multiply').classList.add('text-warning')
      }

      if (num == '/') {
        document.getElementById('divide').classList.remove('text-white')
        document.getElementById('divide').classList.add('bg-white')
        document.getElementById('divide').classList.add('text-warning')
      }
    },

    resetButtons() {
      document.getElementById('plus').classList.remove('bg-white')
      document.getElementById('plus').classList.remove('text-warning')
      document.getElementById('minus').classList.remove('bg-white')
      document.getElementById('minus').classList.remove('text-warning')
      document.getElementById('multiply').classList.remove('bg-white')
      document.getElementById('multiply').classList.remove('text-warning')
      document.getElementById('divide').classList.remove('bg-white')
      document.getElementById('divide').classList.remove('text-warning')

      document.getElementById('plus').classList.add('text-white')
      document.getElementById('minus').classList.add('text-white')
      document.getElementById('multiply').classList.add('text-white')
      document.getElementById('divide').classList.add('text-white')
    },

    clearAll() {
      this.ans = '0'
      this.x = ''
      this.y = ''
      this.prev = ''
      this.resetButtons()
    },

    clearAns() {
      this.ans = '0'
      this.y = ''
    },

    toggleNegative() {
      if (this.ans.charAt(0) != '-') {
        this.ans = '-' + this.ans
      } else {
        this.ans = this.ans.substring(1)
      }
      this.y = this.ans
    },

    setPercentage() {
      let percent = parseFloat(this.ans)/100
      let result = 0

      if (this.x.charAt(this.x.length-1) == '+' || this.x.charAt(this.x.length-1) == '-') {
        result = parseFloat(this.prev * percent).toFixed(3)
      }
      else {
        result = percent.toFixed(3)
      }

      this.ans = String(result)
      this.y = String(result)
    }
  }
}
</script>

<style>
body {
  background-color: #000;
  overflow: hidden;
}

#answer {
    margin-top:24vh;
    color: #fff;
    font-size: 90px;
    
}

.circ {
  width: 80px;
  height: 80px;
    font-size: 35px;
}

.long {
  width: 177px;
  height: 80px;
    font-size: 35px;
}

.bg-grey {
  background-color: #a5a5a5!important
}

.bg-darkgrey {
  background-color: #333!important
}
</style>