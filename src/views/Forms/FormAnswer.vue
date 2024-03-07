<template>
  <div>
    <div class="container mt-10 px-12">
      <div class="text-center">
        <span class="card text-uppercase py-6 fw-bold" style="font-size: 3rem"
          >formulario</span
        >
      </div>
      <div class="card mt-5">
        <div class="row">
          <div class="col-md-5">
            <img
              src="https://img.freepik.com/vector-premium/concepto-prueba-caracter-personas-que-responden-lista-verificacion-cuestionarios-resumen-resultados-exito-examen-linea-formulario-cuestionario-educacion-linea-metafora-encuesta_269730-429.jpg"
              class="img-fluid img-thumbnai text-center"
              style="width: 24rem; height: 24rem; object-fit: cover"
            />
          </div>
          <div class="col-md-5">
            <div
              class="d-flex justify-content-center align-content-center flex-wrap px-12 fs-4"
              style="color: #696969"
            >
              <p>
                Lorem ipsum dolor sit, amet consectetur adipisicing elit.
                Reiciendis eveniet dignissimos nobis optio qui ullam nemo a
                voluptates enim consectetur rem quas, ipsam iste dolore velit
                asperiores architecto eaque minima.
              </p>
            </div>
          </div>
        </div>
      </div>
    </div>

    <div class="container">
      <form @submit.prevent="submitResponse">
        <div class="card mt-12 p-8">
          <label
            :for="'question-' + index"
            class="fs-3 mb-2"
            style="font-weight: 500"
            >pregunta</label
          >
          <input
            type="text"
            class="form-input"
            placeholder="Ingrese su respuesta"
          />
        </div>
        <div class="mt-12 d-flex justify-content-center">
          <button type="submit" class="btn btn-primary">
            Enviar Respuestas
          </button>
        </div>
      </form>
    </div>
  </div>
</template>

<style scoped>
.form-input {
  width: calc(100% - 40px); /* Restar el ancho del botón de eliminar */
  padding: 8px;
  font-size: 16px;
  border: 1px solid #ccc;
  border-radius: 4px;
  outline: none; /* Remueve el borde de foco predeterminado */
  transition: border-color 0.3s ease-in-out, box-shadow 0.3s ease-in-out; /* Suaviza la transición de bordes y sombras */
}

.form-input:focus {
  border-color: #66afe9; /* Cambia el color del borde al enfocar */
  box-shadow: 0 0 8px rgba(102, 175, 233, 0.6); /* Agrega un sombreado sutil */
}
</style>
