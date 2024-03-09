<template>
  <!--begin::Card-->
  <div class="card border border-2 border-gray-300 border-hover">
    <div class="card-header">
      <span class="fs-3 fw-semibold my-2">{{ title }}</span>
    </div>
    <!--end::Name-->

    <!--begin::Description-->
    <p class="text-gray-500 fw-semibold fs-5 mt-1 mb-7">
      {{ getDescription }}
    </p>
    <!--end::Description-->

    <!--begin::Info-->
    <div class="row">
      <div class="col-md-5">
        <!--begin::Due-->
        <div
          class="border border-gray-300 border-dashed rounded min-w-125px py-3 px-4 me-7 mx-1 text-center"
        >
          <div class="fs-6 text-gray-800 fw-bold">{{ getDate }}</div>
          <select class="form-select mt-3">
            <option selected>Forms</option>
          </select>
        </div>
        <!--end::Due-->
      </div>
      <div class="col-md-4">
        <!--begin::Budget-->
        <div
          class="border border-gray-300 border-dashed rounded min-w-125px py-3 px-4 mx-10 text-center"
        >
          <div class="fs-6 text-gray-800 fw-bold">{{ getBudget }}</div>
          <select class="form-select mt-3">
            <option selected>Forms</option>
          </select>
        </div>
        <!--end::Budget-->
      </div>
    </div>
    <!--end::Info-->
  </div>
  <!--end:: Card body-->
  <!--end::Card-->
</template>

<script lang="ts">
import { computed, defineComponent } from "vue";

export default defineComponent({
  name: "card-1",
  components: {},
  props: {
    status: String,

    title: String,

    description: String,

    date: String,

    budget: String,
  },
  setup(props) {
    const getDescription = computed(() => {
      return props.description
        ? props.description
        : "CRM App application to HR efficiency";
    });

    const getDate = computed(() => {
      return props.date ? props.date : "Feb 21, 2021";
    });

    const getBudget = computed(() => {
      return props.budget ? props.budget : "$284,900.00";
    });

    const getStatus = computed(() => {
      return props.status ? props.status : "In Progress";
    });

    return {
      getDescription,
      getDate,
      getBudget,
      getStatus,
    };
  },
});
</script>
