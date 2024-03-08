<template>
  <!--begin::Formulario Widget-->
  <div class="container">
    <div class="row">
      <!-- Sidebar -->
      <div class="col-lg-3">
        <div class="card mb-3">
          <div class="card-header">
            <h4 class="card-title mb-0">Formularios Guardados</h4>
          </div>
          <ul class="list-group list-group-flush">
            <li
              v-for="(savedForm, index) in savedForms"
              :key="index"
              class="list-group-item"
            >
              {{ savedForm.title }}
              <button @click="loadSavedForm(savedForm)" class="btn btn-md">
                <i class="bi bi-cloud-download"></i>
                <!-- Icono de descarga -->
              </button>
              <button @click="removeSavedForm(index)" class="btn btn-md">
                <i class="bi bi-trash"></i>
                <!-- Icono de eliminar -->
              </button>
            </li>
          </ul>
        </div>
      </div>
      <!-- /Sidebar -->
      <div class="col-lg-9">
        <div class="card">
          <div class="card-body py-3">
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
              <button type="submit" class="btn btn-submit">
                Crear Formulario
              </button>
            </form>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { ref, defineComponent } from "vue";

export interface questions {
  pregunta: string;
}
interface SavedForm {
  title: string;
  questions: questions[];
  description: string;
}

export default defineComponent({
  setup() {
    const questions = ref<questions[]>([]);
    const formTitle = ref<string>("");
    const formDesc = ref<string>("");
    const savedForms = ref<SavedForm[]>([]);

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
        description: formDesc.value,
      });

      // Guardar el formulario
      savedForms.value.push({
        title: formTitle.value,
        questions: [...questions.value],
        description: formDesc.value,
      });

      // Limpiar el formulario después de guardar
      clearForm();
    };
    const clearForm = () => {
      formTitle.value = "";
      formDesc.value = "";
      questions.value = [];
    };
    const loadSavedForm = (savedForm: SavedForm) => {
      formTitle.value = savedForm.title;
      formDesc.value = savedForm.description;
      questions.value = [...savedForm.questions];
    };
    const removeSavedForm = (index: number) => {
      savedForms.value.splice(index, 1);
    };

    return {
      addQuestion,
      removeQuestion,
      submitForm,
      questions,
      formTitle,
      formDesc,
      loadSavedForm,
      savedForms,
      removeSavedForm,
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
  color: #dc3545; /* Color de texto */
  border: none; /* Eliminar borde */
  background: none; /* Eliminar fondo */
  padding: 0; /* Eliminar espaciado interno */
  font-size: 14px; /* Tamaño de fuente */
  cursor: pointer; /* Cursor apuntador */
  transition: color 0.3s;
}

.btn:hover {
  opacity: 0.8;
}
</style>
