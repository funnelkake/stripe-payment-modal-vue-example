<template>
  <h1>Vue Demo Application</h1>
  <MDBContainer>
    <div class="row">
      <div class="col-sm-4">
        <div class="card text-center">
          <div class="card-header">Amount Charge</div>
          <div class="card-body">
            <h5 class="card-title">$10</h5>
            <div class="card-text">
              <p>
                Amount set in Admin Panel
              </p>
              <label for="payment-amount-quantity"> Quantity </label>
              <br />
              <select
                id="payment-amount-quantity"
                v-on:change="changeItem('#pm-payment-amount', $event)"
                class="browser-default custom-select"
              >
                <option selected value="1">One</option>
                <option value="2">Two</option>
                <option value="3">Three</option>
              </select>
            </div>
            <button
              type="button"
              id="pm-payment-amount"
              class="btn btn-primary"
            >
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
            <div class="card-text">
              <p>
                Payment with Stripe Price Id
              </p>
              <label for="payment-stripe-id-quantity"> Quantity </label>
              <br />
              <select
                id="payment-stripe-id-quantity"
                v-on:change="changeItem('.pm-payment-stripeid', $event)"
                class="browser-default custom-select"
              >
                <option selected value="1">One</option>
                <option value="2">Two</option>
                <option value="3">Three</option>
              </select>
            </div>
            <button type="button" class="btn btn-primary pm-payment-stripeid">
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
            <div class="card-text">
              <p>
                Subscription Charge
              </p>
              <label for="subscription-quantity"> Quantity </label>
              <br />
              <select
                id="subscription-quantity"
                v-on:change="
                  changeItem('[data-subscription-checkout=true]', $event)
                "
                class="browser-default custom-select"
              >
                <option selected value="1">One</option>
                <option value="2">Two</option>
                <option value="3">Three</option>
              </select>
            </div>
            <button
              type="button"
              class="btn btn-primary"
              data-subscription-checkout="true"
            >
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
  mounted() {
    let externalScript = document.createElement("script");
    externalScript.setAttribute(
      "src",
      `${process.env.VUE_APP_PAYMENT_MODAL_API_HOST_URL}/api/stripe_modals/script.js?siteId=${process.env.VUE_APP_PAYMENT_MODAL_SITE_ID}`
    );
    externalScript.setAttribute("defer", "defer");
    document.body.appendChild(externalScript);
  },
  props: {
    msg: String,
  },
  methods: {
    changeItem: (openModalSelector, event) => {
      const openModalElement = document.querySelector(
        `button${openModalSelector}`
      );
      openModalElement.setAttribute(
        "data-product-quantity",
        event.target.value
      );
    },
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
  box-shadow: lightgray 0px 1px;
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
