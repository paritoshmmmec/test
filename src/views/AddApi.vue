<template>
  <div>
    <section class="section">
      <div class="container">
        <b-field label="Enter the swagger url">
          <b-input placeholder="Endpoint Url" v-model="endpoint" expanded></b-input>
          <p class="control">
            <b-button v-on:click="parse" class="button is-primary">Parse </b-button>
          </p>
        </b-field>
      </div>
    </section>
    <div v-for="e in endpoints" :key="e.id">
      <nav class="panel spacing">
        <p class="panel-heading">
          Endpoint: {{ e.endpointUrl }} <b-tag>{{ e.verb }}</b-tag>
        </p>
        <div class="panel-block is-active">
          <div class="container">
            <b-field label="Team Name">
              <b-input placeholder="Team Name" v-model="e.teamName" expanded></b-input>
            </b-field>
            <b-field label="Slack Handle">
              <b-input
                placeholder="Slack Handle"
                v-model="e.slackHandle"
                expanded
              ></b-input>
            </b-field>
            <b-field label="Description">
              <b-input
                placeholder="Description"
                v-model="e.description"
                type="textarea"
                expanded
              ></b-input>
            </b-field>
          </div>
        </div>
      </nav>
    </div>
    <div class="spacing">
      <button class="button is-link is-outlined is-fullwidth" v-on:click="Save">
        Save
      </button>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
//import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: "Home",
  data() {
    const endpoints = [
      {
        id: 1,
        base: "https://petstore.swagger.io/v2/",
        endpointUrl: "pet/{petId}/uploadImage",
        verb: "POST",
        teamName: "",
        description: "",
        slackHandle: "",
      },
      {
        id: 2,
        base: "https://petstore.swagger.io/v2/",
        endpointUrl: "pet/findByStatus",
        verb: "GET",
        teamName: "",
        description: "",
        slackHandle: "",
      },
    ];
    return {
      labelPosition: "on-border",
      endpoint: "",
      endpoints,
      showDetailIcon: true,
    };
  },
  components: {
    // HelloWorld
  },
  methods: {
    parse: function () {
      console.log(this.endpoint);
      console.log(this.$router);
    },
    Save: function () {
      this.$router.push("/");
    },
  },
};
</script>
<style scoped>
.spacing {
  margin: 20px;
}
</style>
