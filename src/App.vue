<template>
  <q-layout view="hHh lpR fFf">
    <q-header elevated class="header">
      <q-toolbar>
        <q-toolbar-title>
          <div class="logo">Welcome</div>
        </q-toolbar-title>
        <q-btn flat label="Tugas 1" @click="goToTugas1" />
        <q-btn flat label="Tugas 2" @click="goToTugas2" />
        <q-btn flat label="Tugas 3" @click="goToTugas3" />
        <q-btn flat label="Tugas 4" @click="goToTugas4" />
        <q-btn flat label="Tugas 5" @click="goToTugas5" />
        <q-btn flat label="Tugas 6" @click="goToTugas6" />
        <q-btn flat @click="$router.push('/uas')">UAS</q-btn>
      </q-toolbar>
    </q-header>
    <q-page-container>
      <router-view></router-view>
    </q-page-container>
  </q-layout>
</template>

<script>
export default {
  name: 'App',
  methods: {
    goToTugas1() {
      window.location.href = 'https://lambent-basbousa-5f7efa.netlify.app';
    },
    goToTugas2() {
      window.location.href = 'https://tugas2-prak-pbk.netlify.app';
    },
    goToTugas3() {
      window.location.href = 'https://tugasprakpbk3.netlify.app';
    },
    goToTugas4() {
      window.location.href = 'https://tugas4-prak-pbk.netlify.app';
    },
    goToTugas5() {
      window.location.href = 'https://223510175-dickyiswandy.netlify.app';
    },
    goToTugas6() {
      window.location.href = 'https://dickyiswandy-223510175.netlify.app';
    },
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.header {
  background-color: #333;
  color: white;
}
.logo {
  font-size: 24px;
  font-weight: bold;
}
</style>
