<template>
  <div class="assignments">
    <h1 class="assignments__heading">
      Matematikövningar 👨‍🏫
    </h1>
    <form>
      <assignment
        v-for="index in assignments"
        @solved="nextAssignment"
        :key="index" />
    </form>
  </div>
</template>

<script>
import Assignment from './Assignment';

export default {
  components: {
    Assignment,
  },

  data() {
    return {
      assignments: 1,
    };
  },

  methods: {
    nextAssignment() {
      this.assignments += 1;
    },
  },
};
</script>

<style scoped>
.assignments {
  text-align: center;
}

.assignments__heading {
  margin-bottom: 3rem;
}
</style>
