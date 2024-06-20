<template>
    <div>
      <q-card>
        <q-card-section>
          <div class="text-h6">Cuaca Hari Ini</div>
          <div class="q-gutter-md row items-start">
            <q-input v-model="lokasi" label="Masukkan Lokasi" outlined />
            <q-btn color="primary" @click="ambilDataCuaca" label="Cari" class="q-ml-md" />
          </div>
          <div v-if="dataDiambil">
            <div v-if="namaLokasi">
              <div class="text-subtitle1">Lokasi: {{ namaLokasi }}</div>
              <div class="text-h5 q-mt-sm">Temperatur: {{ temperatur }}°C</div>
              <div class="text-subtitle2 q-mt-sm">Deskripsi: {{ deskripsiCuaca }}</div>
            </div>
            <div v-else class="text-subtitle2">Lokasi tidak ditemukan atau terjadi kesalahan.</div>
          </div>
          <div v-else-if="memuat" class="text-subtitle2">Memuat data...</div>
        </q-card-section>
      </q-card>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    name: 'WeatherWidget',
    data() {
      return {
        lokasi: '',
        namaLokasi: '',
        deskripsiCuaca: '',
        temperatur: null,
        memuat: false,
        dataDiambil: false
      };
    },
    methods: {
      async ambilDataCuaca() {
        this.memuat = true;
        this.dataDiambil = false;
        this.namaLokasi = '';
        this.deskripsiCuaca = '';
        this.temperatur = null;
        try {
          const apiKey = 'ee803301abf0db0a9b143c0ff8075caf';
          const apiUrl = `https://api.openweathermap.org/data/2.5/weather?q=${this.lokasi}&appid=${apiKey}&units=metric`;
          const response = await axios.get(apiUrl);
          this.namaLokasi = response.data.name;
          this.deskripsiCuaca = response.data.weather[0].description;
          this.temperatur = response.data.main.temp;
        } catch (error) {
          console.error(error);
        } finally {
          this.memuat = false;
          this.dataDiambil = true;
        }
      }
    }
  };
  </script>
  
  <style>
.text-h6 {
  font-size: 1.25rem;
  font-weight: bold;
  margin-bottom: 1rem;
}

.text-subtitle1 {
  font-size: 1rem;
  font-weight: bold;
}

.text-h5 {
  font-size: 1.5rem;
  margin-top: 0.5rem;
}

.text-subtitle2 {
  font-size: 0.875rem;
  color: #666;
  margin-top: 0.5rem;
}

.q-card {
  max-width: 400px;
  width: 100%;
  margin: auto; /* Untuk memusatkan kotak secara horizontal */
  margin-top: 60px; /* Menambahkan margin atas agar tidak terlalu rapat dengan header */
  padding: 1rem;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  border-radius: 8px;
  background-color: #fff;
}

.q-input {
  width: 100%;
}

.q-btn {
  margin-top: 1rem;
}

.q-btn.primary {
  background-color: #2196f3;
  color: #fff;
}

.q-btn.primary:hover {
  background-color: #0d8bf3;
}

.q-btn.flat {
  color: #2196f3;
  border: 1px solid #2196f3;
  background-color: transparent;
}

.q-btn.flat:hover {
  background-color: #f0f0f0;
}

.q-card-section {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.row {
  display: flex;
  justify-content: center;
  align-items: center;
}

.items-start {
  align-items: flex-start;
}

.items-center {
  align-items: center;
}

.q-mt-sm {
  margin-top: 0.5rem;
}

.q-ml-md {
  margin-left: 1rem;
}

.text-center {
  text-align: center;
}
</style>
