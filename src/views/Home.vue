<template>
  <div class="home">
    <div class="SearchMask">
      <input v-model="gtin" type="text" class="InputField" />
      <button class="search" @click="search">Search</button>
    </div>
      <div v-for="i in currentGtin" :key="i.code">
      <img :src="require(`../assets/Barcodes/${i.artikel}.png`)" class="img" alt="">
      <p><strong>GTIN: </strong>{{ i.code }}</p>
      <p><strong>Artikel: </strong>{{ i.artikel }}</p>
      <p><strong>Betrieb: </strong>{{ i.betrieb }}</p>
      <p><strong>Land: </strong>{{ i.land }}</p>
      <p><strong>Preis: </strong>{{ i.preis }} </p>
      <p><strong>Delivered: </strong>{{ i.delivered }}</p>
      <p><strong>DeliverDate: </strong>{{ i.dilverDate }}</p>
    </div>
  </div>
</template>

<script lang="ts">
export default {
  data() {
    return {
      gtin: "",
      barcodes: [
        {
          code: 7601564111114,
          land: "Schweiz",
          betrieb: "Apple",
          artikel: "Airpods",
          preis: 250,
          delivered: false,
          dilverDate: "09.03.2022",
        },
        {
          code: 7602340111120,
          land: "Schweiz",
          betrieb: "H&M",
          artikel: "TShirt",
          preis: 80,
          delivered: false,
          dilverDate: "09.03.2022",
        },
        {
          code: 7601564113118,
          land: "Schweiz",
          betrieb: "Migros",
          artikel: "Teller",
          preis: 20,
          delivered: true,
          dilverDate: "09.03.2022",
        },
        {
          code: 760156421312,
          land: "Schweiz",
          betrieb: "Apple",
          artikel: "MacBook",
          preis: 1700,
          delivered: false,
          dilverDate: "09.03.2022",
        },
        {
          code: 7604560161435,
          land: "Schweiz",
          betrieb: "Esprit",
          artikel: "Hemd",
          preis: 120,
          delivered: true,
          dilverDate: "09.03.2022",
        }
      ],
      currentGtin: [{
        code: 7601564111114,
          land: "Schweiz",
          betrieb: "Apple",
          artikel: "Airpods",
          preis: 250,
          delivered: false,
          dilverDate: "09.03.2022",
      }],
    };
  },
  methods: {
    search() {
      this.barcodes.forEach((el) => {
        if (el.code.toString() === this.gtin) {
          this.currentGtin.push(el);
          this.currentGtin.splice(0, 1);
        }
      });
    },
    getIMG() {
      return 
    }
  },
};
</script>

<style>
.SearchMask {
  width: 100%;
  height: 80px;
  margin: 0px;
  padding: 0px;
  background-color: rgb(45, 48, 54);
  display: flex;
  justify-content: center;
  align-items: center;
  margin-bottom: 30px;
}
.InputField {
  width: 100%;
  height: 30px;
  margin: 30px;
  font-size: 20px;
  border: none;
}
.search {
  width: 10%;
  height: 30px;
  margin-right: 30px;
}
.img {
  width: 200px;
}
</style>
