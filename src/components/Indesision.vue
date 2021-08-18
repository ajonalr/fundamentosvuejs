<template>
  <img :src="img" alt="Hola Mundo" v-if="img" />
  <div class="gb-darck"></div>
  <div class="indecision-container">
    <input
      type="text"
      name=""
      placeholder="Hasme Una Pregunta"
      v-model="pregunta"
    />
    <p>Recuerda Terminar con (?)</p>

    <div v-if="isvalidQuestion" >
      <h2>{{ pregunta }}</h2>
      <h1>{{ answer  }}</h1>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      pregunta: null,
      answer: null,
      img: null,
      isvalidQuestion: false,
    };
  },

  methods: {
    async getAnswer() {
      this.answer = "Pensando ...!";
      const { answer, image } = await fetch("https://yesno.wtf/api").then((r) =>
        r.json()
      );
      this.answer === 'yes' ? 'SI!' : 'NO!';
      this.img = image;
    },
  },

  watch: {
    pregunta(value, oldvalue) {
      this.isvalidQuestion = false;
      if (!value.includes("?")) {
        return;
      }

      this.isvalidQuestion = true;

      this.getAnswer();
      //realizar peticion Http
    },
  },
};
</script>

<style scoped>
img,
.bg-dark {
  height: 100vh;
  left: 0px;
  max-height: 100%;
  max-width: 100%;
  position: fixed;
  top: 0px;
  width: 100vw;
}

.bg-dark {
  background-color: rgba(0, 0, 0, 0.4);
}

.indecision-container {
  position: relative;
  z-index: 99;
}

input {
  width: 250px;
  padding: 10px 15px;
  border-radius: 5px;
  border: none;
}
input:focus {
  outline: none;
}

p {
  color: white;

  font-size: 20px;
  margin-top: 0px;
}

h1,
h2 {
  color: white;
}

h2 {
  margin-top: 150px;
}
</style>