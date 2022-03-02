<template>
  <div class="container">
    <div class="row justify-content-center">
      <div class="col-xl-7 col-lg-8 col-md-8">
        <div class="card o-hidden border-0 shadow-lg my-2"></div>
        <div class="card-body">
          <div class="row border border-light rounded p-4">
            <div class="h2 mb-3">Donate 😍</div>
            <form class="col-12 p-0" @submit.prevent>
              <div class="form-group">
                <label for="email">Name</label>
                <input
                  type="name"
                  class="form-control"
                  id="name"
                  v-model="name"
                  placeholder="Enter you name"
                />
              </div>
              <div class="form-group">
                <label for="email">Email address</label>
                <input
                  type="email"
                  class="form-control"
                  id="email"
                  v-model="email"
                  placeholder="Enter email"
                />
              </div>
              <div class="form-group">
                <label for="phone">Phone Number</label>
                <input
                  type="tel"
                  class="form-control"
                  id="phone"
                  v-model="phoneNumber"
                  placeholder="Enter email"
                />
              </div>
              <div class="form-group">
                <label for="amount">Amount (₦)</label>
                <input
                  type="number"
                  min="0"
                  class="form-control"
                  id="amount"
                  v-model="amount"
                  placeholder="Amount"
                />
              </div>

              <button type="submit" class="btn btn-primary" @click="submit">
                <i class="fas fa-money-bill-alt"></i>
                Donate
              </button>
            </form>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "WithoutKlashaVue",
  components: {},
  data() {
    return {
      name: "Kola Uche",
      email: "kola.uche@example.com",
      amount: 1000,
      isTestMode: true,
      phoneNumber: "+12138630549",
      merchantKey: "GByi/gkhn5+BX4j6uI0lR7HCVo2NvTsVAQhyPko/uK4=",
      sourceCurrency: "",
      destinationCurrency: "",
      txRef: "" + this.makeId(16),
      businessId: "1",
      paymentDescription: "Donation to a good cause",
      paymentType: "",
    };
  },
  methods: {
    makeId(length) {
      let result = "";
      const characters =
        "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789";
      const charactersLength = characters.length;
      for (let i = 0; i < length; i++) {
        result += characters.charAt(
          Math.floor(Math.random() * charactersLength)
        );
      }
      return result;
    },
    callBack: function (response) {
      console.log(response);
    },
    submit() {
      let kit = {
        currency: this.currency,
        phone_number: this.phoneNumber,
        email: this.email,
        fullname: this.name,
        tx_ref: this.txref,
        callBack: this.callBack,
      };

      var client = new window.klasha(
        this.merchantKey,
        1,
        this.amount,
        "ktest",
        "callback",
        this.currency || "NGN",
        this.sourceCurrency || "NGN",
        kit
      );
      client.init();
    },
  },
  mounted() {
    
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #ffffff;
  margin-top: 60px;
}

@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;700;900&display=swap");

*,
body {
  font-family: "Poppins", sans-serif;
  font-weight: 400;
  -webkit-font-smoothing: antialiased;
  text-rendering: optimizeLegibility;
  -moz-osx-font-smoothing: grayscale;
}

html,
body {
  height: 100%;
  background-color: #152733;
}

.btn-primary {
  background-color: #6c757d;
  outline: none;
  border: 0px;
  box-shadow: none;
}

.btn-primary:hover,
.btn-primary:focus,
.btn-primary:active {
  background-color: #495056 !important;
  outline: none !important;
  border: none !important;
  box-shadow: none !important;
}
</style>
