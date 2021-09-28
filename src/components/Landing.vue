<template>
<div>
    <b-container fluid class="bv-example-row wrapper">
      <b-row>
        <b-col sm="12" md="12">
          <p class="primary">
            <router-link to="/html">General Knowledge</router-link>
          </p>
        </b-col>
        <b-col sm="12" offset-sm="2" md="12" offset-md="0">
          <p class="primary">
            <router-link to="/question2">Computer</router-link>
          </p>
        </b-col>
        <b-col sm="12" offset-sm="2" md="12" offset-md="0">
          <p class="primary">
            <router-link to="/question3">Cartoon & Animation</router-link>
          </p>
        </b-col>
        <b-col sm="12" offset-sm="2" md="12" offset-md="0">
          <p class="primary">
            <router-link to="/question4">Music</router-link>
          </p>
        </b-col>
        <b-col sm="12" offset-sm="2" md="12" offset-md="0">
          <p class="primary">
            <router-link to="/question5">Video Games</router-link>
          </p>
        </b-col>
        <b-col sm="12" offset-sm="2" md="12" offset-md="0">
          <p class="primary">
            <router-link to="/question6">Mathematics</router-link>
          </p>
        </b-col>
        <b-col sm="12" offset-sm="2" md="12" offset-md="0">
          <p class="primary">
            <router-link to="/question7">Sport</router-link>
          </p>
        </b-col>
        <b-col sm="12" offset-sm="2" md="12" offset-md="0">
          <p class="primary">
            <router-link to="/question8">Music</router-link>
          </p>
        </b-col>
        <b-col sm="12" offset-sm="2" md="12" offset-md="0">
          <p class="primary">
            <router-link to="/question9">Science & Nature</router-link>
          </p>
        </b-col>
      </b-row>
    </b-container>
</div>
</template>

<style scoped>
.primary:hover {
    color: #fff;
    background-color: #0766cc;
    border-color: #0062cc;
    text-decoration: none;
    padding: 13px;
}

.primary {
    color: #fff;
    background-color: #0069d9;
    border-color: #0062cc;
    text-decoration: none;
    padding: 10px;
    font-size: 15px;
    border-radius: 5px;
    text-align: center;
}

.primary a{
  color: white;
  font-size: 18px;
  font-weight: 500;
  text-decoration: none;
}

</style>