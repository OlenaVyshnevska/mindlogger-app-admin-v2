<template>
    <b-container class="minW">
      <b-row>
        <b-col>
          <h1 class="text-center">
            <b-img v-if="activityData.meta.logoImage"
            thumbnail
            rounded
            width="75" height="75" blank-color="#777"
            class=""
            :src="getImageURL(activityData.meta.logoImage['@id'])">
            </b-img>
            {{activityData.name}}
          </h1>
        </b-col>
      </b-row>
      <b-row>
        <b-col>
          <p class="lead text-center">
            {{activityData.meta.description}}
          </p>
        </b-col>
      </b-row>
      <b-row>
        <b-col class="text-center">
          <h3>{{activityData.meta.members.editors.length}}</h3>
          <p>Editors</p>
        </b-col>
        <b-col class="text-center">
          <h3>{{activityData.meta.members.managers.length}}</h3>
          <p>Managers</p>
        </b-col>
        <b-col class="text-center">
          <h3>{{activityData.meta.members.users.length}}</h3>
          <p>Users</p>
        </b-col>
        <b-col class="text-center">
          <h3>{{Object.keys(activityData.meta.members.viewers).length}}</h3>
          <p>Reviewers</p>
        </b-col>
        </b-row>
        <b-row>
          <b-col>
            <h2 class="text-center">Group Stats</h2>
            <p class="lead">
              A placeholder for some summary statistics:
            </p>
          </b-col>
        </b-row>
        <b-row>
          <b-col class="text-center">
            <img class="mx-auto w-100 pl-3 pr-3"
            src="../assets/undraw/undraw_data_trends_b0wg.svg"/>
          </b-col>
        </b-row>
    </b-container>
</template>

<style>
  .minW {
    min-width: 300px;
  }
</style>

<script>
import { fullImageURL } from '../api/api';

export default {
  name: 'ActivitySetOverview',
  props: {
    /**
     * activity data from parent route. an object.
     */
    activityData: {
      type: Object,
    },
  },
  methods: {
    /**
     * get the image url from the server.
     */
    getImageURL(id) {
      return fullImageURL(id);
    },
  },
};
</script>
