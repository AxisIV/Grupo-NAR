<template>
  <!--begin::Tables Widget 11-->
  <div class="card">
    <!--begin::Body-->
    <div class="card-body py-3">
      <!--begin::Table container-->
      <div class="table-responsive">
        <!--begin::Table-->
        <table class="table align-middle gs-0 gy-4">
          <!--begin::Table head-->
          <thead>
            <tr class="fw-bold text-muted bg-light">
              <th class="ps-4 min-w-325px rounded-start">Folio</th>
              <th class="min-w-125px">Persona</th>
              <th class="min-w-125px">Fecha Inicio</th>
              <th class="min-w-200px">Último cambio</th>
              <th class="min-w-150px">Status</th>
              <th class="min-w-200px text-end rounded-end"></th>
            </tr>
          </thead>
          <!--end::Table head-->

              <!--begin::Table body for Tab 1-->
              <tbody>
                <!--Your dynamic content for Tab 1-->
                <template v-for="(item, index) in list" :key="index">
                  <tr>
                    <td>
                      <div class="d-flex align-items-center">
                        <div class="d-flex justify-content-start flex-column">
                          <router-link
                            to="/TransaccionesDetails"
                            active-class="active"
                            class="menu-link"
                          >
                            <span
                              class="text-gray-900 fw-bold text-hover-primary mb-1 fs-6"
                              >{{ item.product.name }}</span
                            >
                          </router-link>
                          <span
                            class="text-muted fw-semibold text-muted d-block fs-7"
                            >{{ item.product.specs }}</span
                          >
                        </div>
                      </div>
                    </td>

                    <td>
                      <a
                        href="#"
                        class="text-gray-900 fw-bold text-hover-primary d-block mb-1 fs-6"
                        >{{ item.price }}</a
                      >
                    </td>

                    <td>
                      <a
                        href="#"
                        class="text-gray-900 fw-bold text-hover-primary d-block mb-1 fs-6"
                        >{{ item.deposit }}</a
                      >
                    </td>

                    <td>
                      <a
                        href="#"
                        class="text-gray-900 fw-bold text-hover-primary d-block mb-1 fs-6"
                        >{{ item.agent.name }}</a
                      >
                    </td>

                    <td>
                      <span
                        :class="`badge badge-light-${item.status.color} fs-7 fw-bold`"
                        >{{ item.status.label }}</span
                      >
                    </td>

                    <td class="col-1">
                      <a
                        href="#"
                        class="btn btn-icon btn-bg-light btn-active-color-primary btn-sm me-1"
                      >
                        <KTIcon icon-name="pencil" icon-class="fs-3" />
                      </a>
                      <a
                        href="#"
                        class="btn btn-icon btn-bg-light btn-active-color-primary btn-sm"
                      >
                        <KTIcon icon-name="trash" icon-class="fs-3" />
                      </a>
                    </td>
                  </tr>
                </template>
              </tbody>
              <!--end::Table body for Tab 1-->
            </table>
            <!--end::Table for Tab 1-->
          </div>
          <!--end::Table container for Tab 1-->
        </div>
        <!--end::Tab Pane 1-->

        <!--begin::Tab Pane 2-->
        <div class="tab-pane fade" id="kt_tab_pane_2" role="tabpanel">
          <!--begin::Table container for Tab 2-->
          <div class="table-responsive">
            <!--begin::Table for Tab 2-->
            <table class="table align-middle gs-0 gy-4">
              <!--Table head for Tab 1-->
              <thead>
                <tr class="fw-bold text-muted bg-light">
                  <th class="ps-4 min-w-325px rounded-start">Folio</th>
                  <th class="min-w-125px">Persona</th>
                  <th class="min-w-125px">Fecha Inicio</th>
                  <th class="min-w-200px">Último cambio</th>
                  <th class="min-w-150px">Status</th>
                  <th class="min-w-200px text-end rounded-end"></th>
                </tr>
              </thead>
              <!--end::Table head for Tab 1-->

              <!--begin::Table body for Tab 1-->
              <tbody>
                <!--Your dynamic content for Tab 1-->
                <template v-for="(item, index) in list" :key="index">
                  <tr>
                    <td>
                      <div class="d-flex align-items-center">
                        <div class="d-flex justify-content-start flex-column">
                          <router-link
                            to="/TransaccionesDetails"
                            active-class="active"
                            class="menu-link"
                          >
                            <span
                              class="text-gray-900 fw-bold text-hover-primary mb-1 fs-6"
                              >{{ item.product.name }}</span
                            >
                          </router-link>
                          <span
                            class="text-muted fw-semibold text-muted d-block fs-7"
                            >{{ item.product.specs }}</span
                          >
                        </div>
                      </div>
                    </td>

                    <td>
                      <a
                        href="#"
                        class="text-gray-900 fw-bold text-hover-primary d-block mb-1 fs-6"
                        >{{ item.price }}</a
                      >
                    </td>

                    <td>
                      <a
                        href="#"
                        class="text-gray-900 fw-bold text-hover-primary d-block mb-1 fs-6"
                        >{{ item.deposit }}</a
                      >
                    </td>

                    <td>
                      <a
                        href="#"
                        class="text-gray-900 fw-bold text-hover-primary d-block mb-1 fs-6"
                        >{{ item.agent.name }}</a
                      >
                    </td>

                    <td>
                      <span
                        :class="`badge badge-light-${item.status.color} fs-7 fw-bold`"
                        >{{ item.status.label }}</span
                      >
                    </td>

                    <td class="col-1">
                      <a
                        href="#"
                        class="btn btn-icon btn-bg-light btn-active-color-primary btn-sm me-1"
                      >
                        <KTIcon icon-name="pencil" icon-class="fs-3" />
                      </a>
                      <a
                        href="#"
                        class="btn btn-icon btn-bg-light btn-active-color-primary btn-sm"
                      >
                        <KTIcon icon-name="trash" icon-class="fs-3" />
                      </a>
                    </td>
                  </tr>
                </template>
              </tbody>
              <!--end::Table body for Tab 1-->
            </table>
          </div>
          <!--end::Table container for Tab 2-->
        </div>
        <!--end::Tab Pane 2-->
      </div>
      <!--end::Tab Content-->
    </div>
    <!--end::Body-->
  </div>
  <!--end::Tables Widget 11-->
</template>

<script lang="ts">
import { getAssetPath } from "@/core/helpers/assets";
import { defineComponent } from "vue";

export default defineComponent({
  name: "kt-widget-11",
  components: {},
  props: {
    widgetClasses: String,
  },
  setup() {
    const list = [
      {
        product: {
          name: "#1234",
          specs: "Juan del Toro",
        },
        price: "Fisica",
        deposit: "12/05/2024",
        agent: {
          name: "14/05/2024",
        },
        status: {
          label: "Approved",
          color: "primary",
        },
      },
      {
        product: {
          name: "#0457",
          specs: "Carlos Slim",
        },
        price: "Moral",
        deposit: "22/04/2024",
        agent: {
          name: "05/05/2024",
        },
        status: {
          label: "In Progress",
          color: "danger",
        },
      },
    ];

    return {
      list,
      getAssetPath,
    };
  },
});
</script>
