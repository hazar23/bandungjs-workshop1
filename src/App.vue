<template>
  <div id="hello">
    <img width="25%" src="./assets/logo.png">
    <h1 v-if="isnameShow">Hello saya <span v-html="fistname"></span> {{lastname}}</h1>
    <br>
    <p>
    <input type="text" name="fistname" v-model="fistname">
    <input type="text" name="lastname" v-model="lastname">
    <input type="text" name="city" v-model="address.city">
    <input type="text" name="province" v-model="address.province">
    </p>
    <p>saya tinggal di {{address.city}} {{address.province}}</p>
    <p>tahun depan saya berumur {{age+1}} tahun</p>
    <p>Saya {{work?'bekerja':'tidak bekerja'}}</p>
    <p>
    saya
    <span v-if="age < 10 && age > 0">masih anak kecil</span>
    <span v-else-if="age < 20 && age > 10">sudah remaja</span>
    <span v-else>tua</span>
    </p>
    <p>
    <ul>
    <li v-for="mantan in daftarMantan" :key="mantan.id">
    Teteh {{mantan.namaMantan}}
    </li>
    </ul>
    </p>
    <a v-bind:href="facebookUrl">facebook</a>
    <br>
    <button :disabled="buttonState" v-on:Clik="showPopUp(false)">
    klik saya dong
    </button>
    <button @click="showName">
    Toggle nama
    </button>
    <p>
    umur saya
    {{getMyAge+1}}
    {{getAddressData}}
    </p>
  </div>
</template>

<script>
export default {
  name: "helloWorld",
  data() {
    return {
      fistname: "Hazar",
      lastname: "hamzah",
      work: false,
      age: 11,

      address: {
        city: "Bandung",
        province: "jawa Barat"
      },
      facebookUrl: "https://www.facebook.com/Ooneng23",
      buttonState: true,
      isnameShow: true,
      daftarMantan: [
        { id: 1, namaMantan: "Aurel" },
        { id: 2, namaMantan: "Yayah" },
        { id: 3, namaMantan: "Nanda" }
      ]
    };
  },
  methods: {
    showPopUp(condition) {
      if (condition) {
        alert("saya berisi" + condition);
      } else {
        alert("kamu bernilai" + condition);
      }
    },
    showName() {
      this.isnameShow = !this.isnameShow;
    }
  },
  computed: {
    getAddressData() {
      let { city, province } = this.address;
      return city + " " + province;
    }
  }
};
</script>

<style>
#hello {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
