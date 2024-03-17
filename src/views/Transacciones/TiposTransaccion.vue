<template>
  <div class="container">
    <div class="row">
      <div class="col-md-12">
        <Card />
      </div>
      <Modal />
    </div>
  </div>
</template>

<script>
import Card from "../crafted/pages/profile/Projects.vue";
import Modal from "../crafted/modals/wizards/CreateApp.vue";
export default {
  components: {
    Card,
    Modal,
  },
};
</script>
