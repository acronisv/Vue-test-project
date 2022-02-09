<template>
  <b-container>
    <b-row>
      <b-col><h3>Beer description</h3></b-col>
    </b-row>
    <b-row class="beer-container">
      <b-col md="4">
        <div class="beer-feature">
          <p class="beer-feature__caption">Brand</p>
          <span>{{ beerData.brand }}</span>
        </div>

        <div class="beer-feature">
          <p class="beer-feature__caption">Name</p>
          <span>{{ beerData.name }}</span>
        </div>

        <div class="beer-feature">
          <p class="beer-feature__caption">Style</p>
          <span> {{ beerData.style }}</span>
        </div>
      </b-col>

      <b-col md="4">
        <div class="beer-feature">
          <p class="beer-feature__caption">Hop</p>
          <span>{{ beerData.hop }}</span>
        </div>

        <div class="beer-feature">
          <p class="beer-feature__caption">Yeast</p>
          <span>{{ beerData.yeast }}</span>
        </div>

        <div class="beer-feature">
          <p class="beer-feature__caption">Malts</p>
          <span>{{ beerData.malts }}</span>
        </div>
      </b-col>

      <b-col md="4">
        <div class="beer-feature">
          <p class="beer-feature__caption">Bitterness</p>
          <span>{{ beerData.ibu }}</span>
        </div>

        <div class="beer-feature">
          <p class="beer-feature__caption">Alcohol</p>
          <span>{{ beerData.alcohol }}</span>
        </div>

        <div class="beer-feature">
          <p class="beer-feature__caption">Sugar</p>
          <span>{{ beerData.blg }}</span>
        </div>
      </b-col>
    </b-row>
    <b-row class="btn-container">
      <b-col>
        <b-button variant="outline-primary" v-on:click="methodThatForcesUpdate()">Take a new one</b-button>
      </b-col>
    </b-row>
  </b-container>
</template>

<script>
export default {
  data() {
    return {
      beerData: {
        id: 9153,
        uid: "59115655-8da8-4210-9ed8-010a0269d8e4",
        brand: "Pabst Blue Ribbon",
        name: "Hercules Double IPA",
        style: "Stout",
        hop: "Brewer’s Gold",
        yeast: "1028 - London Ale",
        malts: "Munich",
        ibu: "39 IBU",
        alcohol: "6.1%",
        blg: "13.3°Blg",
      },
    };
  },
  mounted() {
    this.getData();
  },
  methods: {
    getData() {
      fetch("https://random-data-api.com/api/beer/random_beer")
        .then((response) => response.json())
        .then((json) => (this.beerData = json));
    },
    methodThatForcesUpdate() {
      this.$forceUpdate();
      this.getData();
    },
  },
};
</script>

<style>
.beer-container {
  padding: 1.25rem
}
.beer-feature {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
}

.beer-feature__caption {
  font-weight: 700;
}

.beer-description {
  text-align: left;
  font-weight: 700;
  flex-basis: 30%;
}
.beer-data {
  flex-basis: 70%;
  text-align: left;
}
.btn-container {
  margin-bottom: 20px;
}
</style>