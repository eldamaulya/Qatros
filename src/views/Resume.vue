<template>
  <div class="container">
    <h1>Resume</h1>
    <h2>Elda Qotul Maulya</h2>
    <p>Saya adalah seorang mahasiswi semester 7
    Universitas Amikom Yogyakarta
    </p>
    <br>
    <div>
      <h3>Pengalaman</h3>
      <ul class="experience" v-for="exp in experience" :key="exp.id">
        <p class="exp-list" @click="show(exp)">
          {{ exp.id }}. {{ exp.duration }} - {{ exp.position }} di {{ exp.company }}.
        </p>
        <p class="description" v-if="exp.showDesc">{{ exp.description }}</p>
      </ul>
    </div>
    <br>
    <div>
      <h3>Keterampilan</h3>
      <ul>
        <li v-for="skills in skills" :key="skills.skill">
          {{ skills.skill }} {{ skills.percent }}%
          <div class="bar">
            <div class="percent" :style="{ 'width': skills.percent + '%' }"></div>
          </div>
        </li>
      </ul>
    </div>
  <br>
  <div>
    <h3>Kontak Saya</h3>
    <form @submit.prevent="submitContact()" ref="form">
      <p>Nama</p>
      <input type="text" placeholder="Masukkan Nama Lengkap" v-model="nama" required />
      <p>Email</p>
      <input type="email" placeholder="Masukkan Email" v-model="email" required />
      <p>Catatan</p>
      <textarea placeholder="Masukkan Catatan" v-model="note" required />
      <br>
      <button>Submit</button>
    </form>
  </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      experience: [
        {
          id: 1,
          duration: "Agustus 2022 - Sekarang",
          position: "Frontend Web Developer",
          company: "PT. Qatros Teknologi Nusantara",
          description: "Magang",
          showDesc: false,
        },
        {
          id: 2,
          duration: "Februari 2022 - Juli 2022",
          position: "Frontend Web Developer",
          company: "Social Economic Accerelator Lab (SEAL)",
          description: "Studi Independen",
          showDesc: false,
        },
        {
          id: 3,
          duration: "Maret 2021 - Januari 2022",
          position: "Asisten Praktikum",
          company: "Universitas Amikom Yogyakarta",
          description: "Asisten Pendamping Praktikum Dosen",
          showDesc: false,
        },
      ],
      skills: [
        { skill: 'HTML', percent: 80 },
        { skill: 'CSS', percent: 70 },
        { skill: 'PHP', percent: 70 },
      ],

    }
  },
  methods: {
    show(data) {
      data.showDesc = !data.showDesc;
    },

    submitContact() {
      alert(
        "Halo " + this.nama + " , " + this.email + " , " + "Terimakasih Sudah Mengirimkan Catatan " + this.note
      );
      this.$refs.form.reset();
    },
  }
};
</script>

<style>
  .container {
    margin-left: 60%;
    width: 100%;
    background-color: rgb(195, 236, 250);
    border-top-width: 2px;
    border-right-width: 2px;
    border-bottom-width: 2px;
    border-left-width: 2px;
    border-style: solid;
    border-color: rgb(158, 158, 255);
  }

  .bar {
    width: 75%;
    height:20px;
    background-color: #ddd;
    border-radius: 5px;
  }

  .percent {
    height: 100%;
    background-color: #106913;
    border-radius: 5px;
  }

  input, textarea {
    width: 500px;
    height: 100px;
    background-color: rgb(252, 252, 252);
    border-radius: 5px;
  }

  input {
    height: 30px;
  }

  button{ 
  font-size: 20px;                                                  
  padding: 10px ;
  background-color:  rgb(191, 188, 221);
  border-radius: 5px;
  }
</style>                