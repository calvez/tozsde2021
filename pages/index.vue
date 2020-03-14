<template>
  <div>
    <b-container>
      <h1 class="title"></h1>
      <h2 class="subtitle"></h2>
      <b-row>
        <div>
          <Chart></Chart>
        </div>
      </b-row>
      <b-row>
        <b-col md="auto">
          <div>
            <div>
              <b-button-group>
                <b-button>Button 1</b-button>
                <b-button>Button 2</b-button>
                <b-button>Button 3</b-button>
              </b-button-group>
            </div>
            <div class="mt-3">
              <b-button-group>
                <b-button variant="success">Success</b-button>
                <b-button variant="info">Info</b-button>
                <b-button variant="warning">Warning</b-button>
              </b-button-group>
            </div>
            <b-button size="sm" @click="toggle">{{ show ? 'Hide' : 'Show' }} Alert</b-button>
            <b-alert
              v-model="show"
              class="mt-3"
              dismissible
              @dismissed="dismissed"
            >Hello {{ name }}!</b-alert>
          </div>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>
<script>
import Logo from "~/components/Logo.vue";
import Chart from "~/components/Chart.vue";

export default {
  components: {
    Logo,
    Chart
  },
  data() {
    return {
      value: "",
      context: null,
      name: "BootstrapVue",
      show: true
    };
  },
  watch: {
    show(newVal) {
      console.log("Alert is now " + (newVal ? "visible" : "hidden"));
    }
  },
  methods: {
    toggle() {
      console.log("Toggle button clicked");
      this.show = !this.show;
    },
    dismissed() {
      console.log("Alert dismissed");
    },
    onContext(ctx) {
      this.context = ctx;
    }
  }
};
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont,
    "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
