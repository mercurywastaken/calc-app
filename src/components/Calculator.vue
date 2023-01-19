<template>
  <div class="p-3">
    <p id="answer" class="text-end mb-0 me-3">{{ans}}</p>
    <div class="d-flex gap-3 justify-content-center mb-3">
      <button class="circ btn bg-grey text-black rounded-circle d-flex">
        <p class="text-center m-auto p-0" style="font-weight: 500">AC</p>
      </button>
      <button class="circ btn bg-grey text-black rounded-circle d-flex">
        <p class="text-center m-auto p-0"><i class="bi bi-plus-slash-minus"></i></p>
      </button>
      <button class="circ btn bg-grey text-black rounded-circle d-flex">
        <p class="text-center m-auto p-0"><i class="bi bi-percent"></i></p>
      </button>
      <button class="circ btn btn-warning text-white rounded-circle d-flex">
        <p class="text-center m-auto p-0"><i class="fa-solid fa-divide"></i></p>
      </button>
    </div>
    <div class="d-flex gap-3 justify-content-center mb-3">
      <button class="circ btn bg-darkgrey text-white rounded-circle d-flex">
        <p class="text-center m-auto p-0" style="font-weight: 500">7</p>
      </button>
      <button class="circ btn bg-darkgrey text-white rounded-circle d-flex">
        <p class="text-center m-auto p-0" style="font-weight: 500">8</p>
      </button>
      <button class="circ btn bg-darkgrey text-white rounded-circle d-flex">
        <p class="text-center m-auto p-0" style="font-weight: 500">9</p>
      </button>
      <button class="circ btn btn-warning text-white rounded-circle d-flex">
        <p class="text-center m-auto p-0"><i class="fa-solid fa-xmark"></i></p>
      </button>
    </div>
    <div class="d-flex gap-3 justify-content-center mb-3">
      <button class="circ btn bg-darkgrey text-white rounded-circle d-flex">
        <p class="text-center m-auto p-0" style="font-weight: 500">4</p>
      </button>
      <button class="circ btn bg-darkgrey text-white rounded-circle d-flex">
        <p class="text-center m-auto p-0" style="font-weight: 500">5</p>
      </button>
      <button class="circ btn bg-darkgrey text-white rounded-circle d-flex">
        <p class="text-center m-auto p-0" style="font-weight: 500">6</p>
      </button>
      <button class="circ btn btn-warning text-white rounded-circle d-flex">
        <p class="text-center m-auto p-0"><i class="fa-solid fa-minus"></i></p>
      </button>
    </div>
    <div class="d-flex gap-3 justify-content-center mb-3">
      <button class="circ btn bg-darkgrey text-white rounded-circle d-flex">
        <p class="text-center m-auto p-0" style="font-weight: 500">1</p>
      </button>
      <button class="circ btn bg-darkgrey text-white rounded-circle d-flex">
        <p class="text-center m-auto p-0" style="font-weight: 500">2</p>
      </button>
      <button class="circ btn bg-darkgrey text-white rounded-circle d-flex">
        <p class="text-center m-auto p-0" style="font-weight: 500">3</p>
      </button>
      <button class="circ btn btn-warning text-white rounded-circle d-flex">
        <p class="text-center m-auto p-0"><i class="fa-solid fa-plus"></i></p>
      </button>
    </div>
    <div class="d-flex gap-3 justify-content-center mb-3">
      <button class="long btn bg-darkgrey text-white rounded-pill d-flex">
        <p class="text-start ms-3 my-auto p-0" style="font-weight: 500">0</p>
      </button>
      <button class="circ btn bg-darkgrey text-white rounded-circle d-flex">
        <p class="text-center m-auto p-0" style="font-weight: 500">.</p>
      </button>
      <button class="circ btn btn-warning text-white rounded-circle d-flex">
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
      ans: 0,
      first: 0,
      second: 0,
      operator: ''
    }
  },
  methods: {
    
  }
}
</script>

<style>
body {
    background-color: #000
}

#answer {
    margin-top:23vh;
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