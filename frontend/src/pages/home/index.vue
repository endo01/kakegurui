<template>
  <div class="auth-layout row align-content--center">
    <div class="flex xs12 pa-3">
      <div class="d-flex justify--center">
        <va-card class="__card">
          <va-card-content>
            <div class="column">
              <va-input
                class="mb-4"
                v-model="value"
                :messages="message"
                label="Name"
                placeholder="eg. endo"
              />
              <div>
                <va-button color="success" @click="createRoom">
                  <pre>Create</pre>
                </va-button>
              </div>
              <div>
                <va-button color="info" @click="joinRoom">
                  <pre> Join </pre>
                </va-button>
              </div>
            </div>
          </va-card-content>
        </va-card>
      </div>
    </div>
  </div>
</template>

<script>
import _ from "lodash";

export default {
  name: "home",
  data() {
    return {
      //data to return
    };
  },
  methods: {
    createRoom() {
      //call new route to create room
    },
    joinRoom() {
      // call new route to join room
    }
  }
};
</script>

<style scoped>
.on-hover {
  border: 1px solid black;
}

.column > div {
  margin: 0.1em;
  padding: 0.3em 1em;
  display: flex;
  justify-content: center;
}
</style>
