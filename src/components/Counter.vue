<template>
  <h2>{{customTitle}}</h2>
  <p>{{ counter }} <sup>2</sup> = {{ squareCounter }}</p>

  <div>
    <button @click="sumar()">+1</button>
    <button @click="restar()">-1</button>
  </div>
</template>

<script>
export default {
   props: {
      title: {
         String,
         require: true
      },
      star: {
         Number,
         default: 100,
         // require: true
         validator (valor) {
            return valor  > 0;
         }
      }
   },
  data() {
    return {
      counter: this.star,
    };
  },
  methods: {
    sumar() {
       
      this.counter ++;
    },
    restar() {
       this.counter --;
    }
  },
  computed: {
    squareCounter() {
      return this.counter * this.counter;
    },
    customTitle() {
      return this.title ? this.title : 'Salieron';
    }
  },
};
</script>

<style scoped>
button {
  background-color: #64bb87;
  border-radius: 5px;
}
</style>