<template>
  <div id="app" class="min-h-screen w-full bg-gray-200 flex flex-col items-center">
    <button
      @click="triggerTransition"
      class="my-10 bg-transparent hover:bg-blue-500 text-blue-700 font-semibold hover:text-white py-2 px-4 border border-blue-500 hover:border-transparent rounded"
    >Enlighten me</button>
    <template v-if="showPayments">
      <staggered-fade :duration="150" tag="ul" class="flex flex-col w-full items-center max-w-md">
        <!-- Each element requires a data-index attribute in order for the transition to work properly -->
        <payment-card
          v-for="(payment, index) in payments"
          :payment="payment"
          :data-index="index"
          :key="payment.name"
        />
      </staggered-fade>
    </template>
  </div>
</template>

<script>
import PaymentCard from "./components/PaymentCard";
import StaggeredFade from "./components/StaggeredFade";
export default {
  name: "App",
  components: {
    PaymentCard,
    StaggeredFade
  },
  data() {
    return {
      showPayments: true,
      payments: [
        {
          image:
            "https://cdn-media-1.freecodecamp.org/images/0*xkJgg-6HskYrQ3N7.jpeg",
          name: "Evan You",
          amount: "5",
          currency: "Hooks",
          statusColor: "green",
          statusText: "vuesed"
        },
        {
          image:
            "https://www.sapeople.com/wp-content/uploads/2015/09/elon-th.jpg",
          name: "Jeff Bezos",
          currency: "CyberTrucks",
          amount: "666",
          statusColor: "orange",
          statusText: "flying to mars"
        },
        {
          image: "https://developeronfire.com/assets/images/UncleBobMartin.jpg",
          name: "StackOverflow",
          currency: "Patterns",
          amount: "3",
          statusColor: "blue",
          statusText: "in review"
        },
        {
          image:
            "https://pbs.twimg.com/profile_images/988775660163252226/XpgonN0X_400x400.jpg",
          name: "Steve Jobs",
          currency: "Surface Books",
          amount: "2019",
          statusColor: "red",
          statusText: "delayed forever"
        },
        {
          image:
            "https://yt3.ggpht.com/a/AATXAJwIHOTspfmIL24Bcr_aIor6CI-Q0zifWQ7vIA=s900-c-k-c0xffffffff-no-rj-mo",
          name: "Youtube",
          currency: "Phones",
          amount: "123",
          statusColor: "green",
          statusText: "approved"
        }
      ]
    };
  },
  methods: {
    // You probably won't need this
    triggerTransition() {
      this.showPayments = false;
      this.$nextTick(() => {
        this.showPayments = true;
      });
    }
  }
};
</script>

<style>
</style>
