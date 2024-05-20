<template>
  <v-container class="text-center">
    <v-row justify="center">
      <v-col cols="12" md="4" sm="6" v-for="(action, index) in actions" :key="index">
        <v-btn 
          :color="action.color" 
          dark :rounded="action.rounded" size="x-large" block 
          @click="handleActionClick(action)"
          @mouseover="toggleColors(index)"
          :style="{ backgroundColor: action.currentColor }">
          {{ action.label }}
        </v-btn>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      actions: [
        // Tus otras acciones...
        { label: 'Agregar Curso', route: '/add_course', color: 'blue darken-2', rounded: '0', currentColor: 'blue darken-2' },
        // Tus otras acciones...
      ]
    };
  },
  methods: {
    handleActionClick(action) {
      if (action.route === '/add_course') {
        this.$router.push(action.route);
      } else {
        // Aquí puedes manejar otras acciones si es necesario
      }
    },
    toggleColors(index) {
      const tempColor = this.actions[index].color;
      this.actions[index].color = this.actions[index].currentColor;
      this.actions[index].currentColor = tempColor;
    }
  }
};
</script>

<style scoped>
</style>
