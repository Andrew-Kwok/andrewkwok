<script setup>

const achievements = [
  {
    "id": 1,
    "title": "First Achievement",
    "description": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec auctor, nisl eu ultricies fermentum, nunc libero ultricies urna, eget ultricies velit nisl eu nunc. Sed vitae nisl eget nunc aliquam aliquet. Sed vitae nisl eget nunc aliquam aliquet.",
    "color": "blue",
    "icon": "mdi-trophy"
  },
  {
    "id": 2,
    "title": "Second Achievement",
    "description": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec auctor, nisl eu ultricies fermentum, nunc libero ultricies urna, eget ultricies velit nisl eu nunc. Sed vitae nisl eget nunc aliquam aliquet. Sed vitae nisl eget nunc aliquam aliquet.",
    "color": "red",
    "icon": "mdi-trophy"
  },
  {
    "id": 3,
    "title": "Third Achievement",
    "description": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec auctor, nisl eu ultricies fermentum, nunc libero ultricies urna, eget ultricies velit nisl eu nunc. Sed vitae nisl eget nunc aliquam aliquet. Sed vitae nisl eget nunc aliquam aliquet.",
    "color": "yellow",
    "icon": "mdi-trophy"
  }
]


</script>

<template>
  <div id="achievement" class="h-screen flex justify-center items-center">
    <p class="text-7xl"> achievements </p>
  </div>

<!--  <div id="achievements" :style="`height: calc(100vh - ${navbarHeight}px)`" class="h-screen flex justify-center items-center">-->
<!--    <v-timeline direction="horizontal">-->
<!--      <v-timeline-item>-->
<!--        <template v-slot:opposite>-->
<!--          Opposite content-->
<!--        </template>-->
<!--        <div>-->
<!--          <div class="text-h6">Content title</div>-->
<!--          <p>-->
<!--            Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.-->
<!--          </p>-->
<!--        </div>-->
<!--      </v-timeline-item>-->

<!--      <v-timeline-item>-->
<!--        <template v-slot:opposite>-->
<!--          Opposite content-->
<!--        </template>-->
<!--        <div>-->
<!--          <div class="text-h6">Content title</div>-->
<!--          <p>-->
<!--            Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.-->
<!--          </p>-->
<!--        </div>-->
<!--      </v-timeline-item>-->

<!--      <v-timeline-item>-->
<!--        <template v-slot:opposite>-->
<!--          Opposite content-->
<!--        </template>-->
<!--        <div>-->
<!--          <div class="text-h6">Content title</div>-->
<!--          <p>-->
<!--            Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.-->
<!--          </p>-->
<!--        </div>-->
<!--      </v-timeline-item>-->
<!--    </v-timeline>-->
<!--  </div>-->

</template>

<style scoped>

</style>