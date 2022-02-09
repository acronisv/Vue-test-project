<template>
  <div class="container">
    <h2>User profile</h2>
    <b-tabs pills card justified >
      <b-tab title="User" active>
        <b-card-text>
          <b-row>
            <b-col>
              <h3>{{ userData.first_name }} {{ userData.last_name }}</h3>
            </b-col>
          </b-row>
          <b-row>
            <b-col md="6">
              <img :src=userData.avatar alt="">
            </b-col>
            <b-col md="6" class="user-tab">
              <div class="user-tab__line">
                <p class="user-tab__caption">Username</p>
                <span class="user-tab__line-data">{{ userData.username }}</span>
              </div>
              <div class="user-tab__line">
                <p class="user-tab__caption">E-mail</p>
                <a class="user-tab__line-data" :href="`mailto:${userData.email}`">{{ userData.email }}</a>
              </div>
              <div class="user-tab__line">
                <p class="user-tab__caption">Phone</p>
                <a class="user-tab__line-data" :href="`tel:${userData.phone_number}`">{{ userData.phone_number }}</a>
              </div>
              <div class="user-tab__line">
                <p class="user-tab__caption">Gender</p>
                <span class="user-tab__line-data">{{ userData.gender }}</span>
              </div>
              <div class="user-tab__line">
                <p class="user-tab__caption">Insurance</p>
                <span class="user-tab__line-data">{{ userData.social_insurance_number }}</span>
              </div>
              <div class="user-tab__line">
                <p class="user-tab__caption">Birthday</p>
                <span class="user-tab__line-data">{{ userData.date_of_birth }}</span>
              </div>
            </b-col>
          </b-row>
      </b-card-text>
      </b-tab>
      <b-tab title="Address">
        <b-card-text>
          <b-row>
            <b-col md="6" class="user-tab">
                <div class="user-tab__line">
                  <p class="user-tab__caption">City</p>
                  <span class="user-tab__line-data">{{ userData.address.city }}</span>
                </div>
                <div class="user-tab__line">
                  <p class="user-tab__caption">Street</p>
                  <span class="user-tab__line-data">{{ userData.address.street_name }}</span>
                </div>
                <div class="user-tab__line">
                  <p class="user-tab__caption">Address</p>
                  <span class="user-tab__line-data">{{ userData.address.street_address }}</span>
                </div>
                <div class="user-tab__line">
                  <p class="user-tab__caption">Zip code</p>
                  <span class="user-tab__line-data">{{ userData.address.zip_code }}</span>
                </div>
                <div class="user-tab__line">
                  <p class="user-tab__caption">State</p>
                  <span class="user-tab__line-data">{{ userData.address.state }}</span>
                </div>
                <div class="user-tab__line">
                  <p class="user-tab__caption">Country</p>
                  <span class="user-tab__line-data">{{ userData.address.country }}</span>
                </div>
                <div class="user-tab__line">
                  <p class="user-tab__caption">Latitude</p>
                  <span class="user-tab__line-data">{{ userData.address.coordinates.lat }}</span>
                </div>
                <div class="user-tab__line">
                  <p class="user-tab__caption">Longitude</p>
                  <span class="user-tab__line-data">{{ userData.address.coordinates.lng }}</span>
                </div>
            </b-col>
          </b-row>
        </b-card-text>
      </b-tab>
      <b-tab title="Employment">
        <b-card-text>
          <b-row>
            <b-col md="6" class="user-tab">
              <div class="user-tab__line">
                <p class="user-tab__caption">Title</p>
                <span class="user-tab__line-data">{{ userData.employment.title }}</span>
              </div>
              <div class="user-tab__line">
                <p class="user-tab__caption">Skills</p>
                <span class="user-tab__line-data">{{ userData.employment.key_skill }}</span>
              </div>
            </b-col>
          </b-row>
        </b-card-text>
      </b-tab>
      <b-tab title="Payment">
        <b-card-text>
          <b-row>
            <b-col md="6" class="user-tab">
                <div class="user-tab__line">
                  <p class="user-tab__caption">Credit card</p>
                  <span class="user-tab__line-data">{{ userData.credit_card.cc_number }}</span>
                </div>
            </b-col>
          </b-row>
        </b-card-text>
      </b-tab>
      <b-tab title="Subscription">
         <b-card-text>
           <b-row>
            <b-col md="6" class="user-tab">
                <div class="user-tab__line">
                  <p class="user-tab__caption">Plan</p>
                  <span class="user-tab__line-data">{{ userData.subscription.plan }}</span>
                </div>
                <div class="user-tab__line">
                  <p class="user-tab__caption">Status</p>
                  <span class="user-tab__line-data">{{ userData.subscription.status }}</span>
                </div>
                <div class="user-tab__line">
                  <p class="user-tab__caption">Payment method</p>
                  <span class="user-tab__line-data">{{ userData.subscription.payment_method }}</span>
                </div>
                <div class="user-tab__line">
                  <p class="user-tab__caption">Terms</p>
                  <span class="user-tab__line-data">{{ userData.subscription.term }}</span>
                </div>
            </b-col>
          </b-row>
        </b-card-text>
      </b-tab>
    </b-tabs>
  </div>
</template>

<script>

export default {
  data() {
    return {
      userData: [],
    };
  },
  mounted() {
    fetch("https://random-data-api.com/api/users/random_user")
      .then((response) => response.json())
      .then((json) => (this.userData = json));
  },
};
</script>
<style>
.user-tab {
  display: flex;
  flex-direction: column;
  margin: 10px auto;
}
.user-tab__line {
  display: flex;
  text-align: left;
}

.user-tab__caption {
  font-weight: 700;
  flex-basis: 30%;
}

.user-tab__line-data {
  margin: 0 0 0 auto;
  word-wrap: break-word;
  overflow: hidden;
  text-align: right;
}

</style>