<template>
  <div class="form-container">
    <form @submit.prevent="submitForm">
      <div class="form-group">
        <input
          type="text"
          v-model="formTitle"
          class="form-title"
          placeholder="Formulario sin título"
        />
        <textarea
          id="form-title"
          v-model="formDesc"
          class="form-title-input"
          placeholder="Ingrese una descripción para el formulario"
        ></textarea>
      </div>
      <div
        v-for="(question, index) in questions"
        :key="index"
        class="form-group"
      >
        <label :for="'question-' + index" class="form-label"
          >Pregunta {{ index + 1 }}:</label
        >
        <input
          type="text"
          :id="'question-' + index"
          v-model="questions[index].pregunta"
          class="form-input"
          placeholder="Ingrese una pregunta"
        />
        <button
          type="button"
          @click="removeQuestion(index)"
          class="btn btn-remove"
        >
          X
        </button>
      </div>
      <button type="button" @click="addQuestion" class="btn btn-add">
        Agregar Pregunta
      </button>
      <button type="submit" class="btn btn-submit">Crear Formulario</button>
    </form>
  </div>
</template>

<script lang="ts">
import { ref, defineComponent } from "vue";

export interface questions {
  pregunta: string;
}

export default defineComponent({
  setup() {
    const questions = ref<questions[]>([]);
    const formTitle = ref<string>("");
    const formDesc = ref<string>("");

    const addQuestion = () => {
      questions.value.push({
        pregunta: "Pregunta",
      });
    };

    const removeQuestion = (index: number) => {
      questions.value.splice(index, 1);
    };

    const submitForm = () => {
      // Aquí puedes enviar el formulario o hacer lo que necesites con las preguntas
      console.log("Formulario enviado:", {
        title: formTitle.value,
        questions: questions.value,
        Descripcion: formDesc.value,
      });
    };

    return {
      addQuestion,
      removeQuestion,
      submitForm,
      questions,
      formTitle,
      formDesc,
    };
  },
});
</script>

<style scoped>
.form-container {
  max-width: 500px;
  margin: 0 auto;
}

.form-group {
  margin-bottom: 20px;
  position: relative; /* Añadir posición relativa para que el botón de eliminar esté posicionado correctamente */
}

.form-label {
  font-weight: bold;
  margin-bottom: 5px;
  display: block;
}

.form-title-input,
.form-input {
  width: calc(100% - 40px); /* Restar el ancho del botón de eliminar */
  padding: 8px;
  font-size: 16px;
  border: 1px solid #ccc;
  border-radius: 4px;
}

.form-title {
  border: none;
  outline: none;
  background-color: transparent;
  font-size: 20px;
}

.btn {
  padding: 10px 20px;
  font-size: 16px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.btn-add {
  background-color: #4caf50;
  color: white;
  margin-right: 10px;
}

.btn-submit {
  background-color: #008cba;
  color: white;
}

.btn-remove {
  background-color: #f44336;
  color: white;
  margin-left: 10px;
}

.btn:hover {
  opacity: 0.8;
}
</style>
