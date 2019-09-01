<template>
  <div class="assignments">
    <h1 class="assignments__heading">
      Math Training
    </h1>
    <form>
      <transition-group name="assignments" tag="div">
        <assignment
          v-for="index in assignments"
          @solved="nextAssignment"
          :key="index" />
      </transition-group>
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
      window.scrollTo(0, document.body.scrollHeight);
    },
  },
};
</script>

<style scoped>
.assignments {
  text-align: center;
  padding-bottom: 10rem;
}

.assignments__heading {
  font-family: 'Chalkduster', Helvetica, sans-serif;
  font-size: 3rem;
  margin-bottom: 3rem;
}

/* Transitions */
.assignments-enter-active, .assignments-leave-active {
  transition: all 0.5s;
}

.assignments-enter, .assignments-leave-to {
  opacity: 0;
}
</style>
