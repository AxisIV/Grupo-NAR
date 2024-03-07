<template>
  <div class="container">
    <div class="form-response">
      <h2>titulo</h2>
    </div>
    <div class="form-response">
      <p>descripcion</p>
    </div>

    <form @submit.prevent="submitResponse">
      <div class="form-group">
        <label :for="'question-' + index" class="form-label">pregunta</label>
        <input
          type="text"
          class="form-input"
          placeholder="Ingrese su respuesta"
        />
      </div>
      <button type="submit" class="btn btn-submit">Enviar Respuestas</button>
    </form>
  </div>
</template>

<!-- <template>
    <div class="form-response">
      <h2>{{ title }}</h2>
      <p>{{ description }}</p>
      <form @submit.prevent="submitResponse">
        <div v-for="(question, index) in questions" :key="index" class="form-group">
          <label :for="'question-' + index" class="form-label">{{ question }}</label>
          <input
            type="text"
            :id="'question-' + index"
            v-model="responses[index]"
            class="form-input"
            placeholder="Ingrese su respuesta"
          />
        </div>
        <button type="submit" class="btn btn-submit">Enviar Respuestas</button>
      </form>
    </div>
  </template> -->

<script>
// export default {
//   props: {
//     title: String,
//     description: String,
//     pregunta: Array,
//   },
//   data() {
//     return {
//       responses: Array(this.questions.length).fill(""),
//     };
//   },
//   methods: {
//     submitResponse() {
//       // Aquí puedes manejar el envío de las respuestas
//       console.log("Respuestas enviadas:", this.responses);
//       // Puedes realizar alguna acción adicional aquí, como enviar las respuestas a través de una solicitud HTTP
//     },
//   },
// };
</script>

<style scoped>
.container {
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
}
.form-response {
  max-width: 500px;
  margin: 0 auto;
  margin-top: 10px;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 8px;
}

.form-response h2 {
  margin-bottom: 10px;
}

.form-response p {
  margin-bottom: 20px;
}

.form-group {
  margin-bottom: 20px;
}

.form-label {
  font-weight: bold;
  margin-bottom: 5px;
}

.form-input {
  width: 100%;
  padding: 8px;
  font-size: 16px;
  border: 1px solid #ccc;
  border-radius: 4px;
}

.btn {
  padding: 10px 20px;
  font-size: 16px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  background-color: #008cba;
  color: white;
}

.btn-submit:hover {
  opacity: 0.8;
}
</style>
