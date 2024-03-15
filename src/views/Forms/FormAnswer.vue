<template>
  <div class="form">
    <div class="container mt-10 px-12">
      <div class="text-center">
        <h1 class="card text-uppercase py-6 fw-bold" style="font-size: 3rem">
          {{ formData.title }}
        </h1>
      </div>
      <div class="card mt-5">
        <div class="row">
          <div class="col-md-5">
            <img
              src="https://img.freepik.com/vector-premium/concepto-prueba-caracter-personas-que-responden-lista-verificacion-cuestionarios-resumen-resultados-exito-examen-linea-formulario-cuestionario-educacion-linea-metafora-encuesta_269730-429.jpg"
              class="img-fluid img-thumbnail text-center"
              style="width: 24rem; height: 24rem; object-fit: cover"
            />
          </div>
          <div class="col-md-5">
            <p>{{ formData.description }}</p>
          </div>
        </div>
      </div>
      <div class="card mt-5">
        <div>
          <div
            v-for="(question, index) in formData.questions"
            :key="index"
            class="d-flex justify-content-center align-content-center flex-wrap px-12 fs-4"
          >
            <label>{{ question.pregunta }}</label>
            <template v-if="question.tipo === 'text'">
              <input
                type="text"
                v-model="respuestas[index]"
                class="form-control form-input"
                placeholder="Ingrese su respuesta"
              />
            </template>
            <template v-else-if="question.tipo === 'radio'">
              <div
                v-for="(opcion, opcIndex) in question.opciones"
                :key="opcIndex"
              >
                <input
                  type="radio"
                  :id="'opcion-' + index + '-' + opcIndex"
                  :value="opcion.valor"
                  v-model="respuestas[index]"
                  class="form-check-input"
                />
                <label
                  :for="'opcion-' + index + '-' + opcIndex"
                  class="form-check-label"
                  >{{ opcion.nombre }}</label
                >
              </div>
            </template>
          </div>
        </div>
      </div>
    </div>

    <div class="container mt-5">
      <form @submit.prevent="submitResponse">
        <div class="card p-4">
          <label class="fs-5 mb-2" style="font-weight: 500">Respuestas</label>
          <div v-for="(respuesta, index) in respuestas" :key="index">
            <p>{{ index + 1 }}. {{ respuesta }}</p>
          </div>
        </div>
        <div class="mt-4 d-flex justify-content-center">
          <button type="submit" class="btn btn-primary btn-lg">
            Enviar Respuestas
          </button>
        </div>
      </form>
    </div>
  </div>
</template>

<script lang="ts">
import { ref } from "vue";

export default {
  data() {
    return {
      formData: {
        title: "Encuesta de Satisfacción",
        description:
          "Por favor, responda a las siguientes preguntas para evaluar su experiencia con nuestros servicios.",
        questions: [
          {
            tipo: "text",
            pregunta: "¿Cuál es su nombre?",
          },
          {
            tipo: "radio",
            pregunta: "¿Cómo calificaría nuestro servicio?",
            opciones: [
              { nombre: "Excelente", valor: "5" },
              { nombre: "Muy Bueno", valor: "4" },
              { nombre: "Bueno", valor: "3" },
              { nombre: "Regular", valor: "2" },
              { nombre: "Malo", valor: "1" },
            ],
          },
          {
            tipo: "text",
            pregunta:
              "¿Tiene algún comentario adicional que quisiera compartir con nosotros?",
          },
        ],
      },
      respuestas: [],
    };
  },
  methods: {
    submitResponse() {
      console.log("Respuestas enviadas:", this.respuestas);
      // Aquí puedes hacer algo con las respuestas, como enviarlas a un servidor
    },
  },
};
</script>

<style scoped>
.form {
  max-width: 940px;
  margin: 30px auto;
  background: wheat;
  text-align: left;
  padding: 40px;
  border-radius: 10px;
}
label {
  color: #726f6f;
  display: inline-block;
  margin: 25px 0 15px;
  font-size: 1em;
  text-transform: uppercase;
  letter-spacing: 1px;
  font-weight: bold;
}
.form-input {
  display: block;
  padding: 10px 6px;
  width: 100%;
  box-sizing: border-box;
  font-size: 16px;
  border: 1px solid #ccc;
  border-radius: 4px;
  color: #555;
  transition: border-color 0.3s ease-in-out, box-shadow 0.3s ease-in-out;
  margin-bottom: 15zpx;
}

.form-input:focus {
  border-color: #66afe9;
  box-shadow: 0 0 8px rgba(102, 175, 233, 0.6);
}
.form-check {
  margin-bottom: 10px; /* Espacio entre cada opción */
}

.form-check-input {
  margin-right: 5px; /* Espacio entre el input y el label */
  cursor: pointer; /* Cambiar cursor al pasar sobre el input */
}

.form-check-label {
  display: block;
  cursor: pointer; /* Cambiar cursor al pasar sobre el label */
}
</style>
