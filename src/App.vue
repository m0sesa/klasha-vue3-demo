<template>
  <div class="container">
    <div class="row justify-content-center">
      <div class="col-xl-7 col-lg-8 col-md-8">
        <div class="card o-hidden border-0 shadow-lg my-0"></div>
        <div class="card-body">
          <div class="row border border-light rounded p-4">
            <div class="h3">Options</div>
            <ul>
              <li><router-link to="/without-klasha-vue">Without Klasha Vue Integration</router-link></li>
              <li><router-link to="/with-klasha-vue">With Klasha Vue Integraton</router-link></li>
            </ul>
          </div>
        </div>
      </div>
    </div>
    <router-view></router-view>
  </div>
</template>

<script>
// import klasha from "vue3-klasha";

export default {
  name: "App",
  components: {
    // klasha,
  },
  data() {
    return {
      name: "Kola Buhari",
      email: "kola.buhari@example.com",
      amount: 1000, 
      isTestMode: true,
      phoneNumber: "",
      merchantKey: "GByi/gkhn5+BX4j6uI0lR7HCVo2NvTsVAQhyPko/uK4=",
      sourceCurrency: "" || "NGN",
      destinationCurrency: "" || "NGN",
      txRef: "" + this.makeId(16),
      businessId: "1",
      paymentDescription: "Donation to a good cause",
      paymentType: "",
    };
  },
  computed: {
    amountKobo(){
      return this.amount*100;
    }
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
  },
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

a{
  color: #c0c0c0;
}

a:hover{
  color: #ffffff;
}
</style>
