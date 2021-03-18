<template>
  <h1>Vue Demo Application</h1>
  <MDBContainer>
    <div class="row">
      <div class="col-sm-4">
        <div class="card text-center">
          <div class="card-header">Amount Charge</div>
          <div class="card-body">
            <h5 class="card-title">$10</h5>
            <p class="card-text">
              Amount set in Admin Panel
            </p>
            <button type="button" class="btn btn-primary">
              Amount Charge
            </button>
          </div>
        </div>
      </div>
      <div class="col-sm-4">
        <div class="card text-center">
          <div class="card-header">Stripe Price Charge</div>
          <div class="card-body">
            <h5 class="card-title">$39</h5>
            <p class="card-text">
              Payment with Stripe Price Id
            </p>
            <button type="button" class="btn btn-primary">
              Stripe Price Charge
            </button>
          </div>
        </div>
      </div>
      <div class="col-sm-4">
        <div class="card text-center">
          <div class="card-header">Subscription</div>
          <div class="card-body">
            <h5 class="card-title">$49<small>/mo</small></h5>
            <p class="card-text">
              Subscription Charge
            </p>
            <button type="button" class="btn btn-primary">
              Subscribe
            </button>
          </div>
        </div>
      </div>
    </div>
  </MDBContainer>
</template>

<script>
import { MDBContainer } from "mdb-vue-ui-kit";

export default {
  name: "Demo",
  components: {
    MDBContainer,
  },
  props: {
    msg: String,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1 {
  text-align: center;
  padding: 80px;
}
.card-header {
  background-color: #616161;
  padding: 16px;
  color: black;
  font-size: 24px;
  font-weight: 400;
}
.card {
  border-radius: 8px;
}
.card-title {
  padding-top: 20px;
  font-size: 3rem;
}
.card-body {
  padding: 0px;
}
.card-text {
  padding: 16px;
}
.btn {
  margin: 16px;
}
</style>
