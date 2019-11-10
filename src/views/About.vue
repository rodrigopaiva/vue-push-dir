<template>
  <div class="about">
    <h1>Find Places</h1>

    <p>This page is for find places around you!</p>

    <input id="pac-input" type="text" name="address" placeholder="Type Address" class="form-control controls" required />
    <div id="map"></div>
  </div>
</template>

<script>
export default {
  created () {
    // embed script for google maps api
    let ckeditor = document.createElement('script')
    ckeditor.setAttribute('src', 'https://maps.googleapis.com/maps/api/js?key=AIzaSyBMHI7Ds0I7NZVA55NSW1ziaoe1fuOLMVE&libraries=places&callback=initAutocomplete')
    document.head.appendChild(ckeditor)
  }
}
</script>

<style>
    form {
      width: 55%;
      margin: 0 auto;
    }

    #map {
      height: 450px;
    }

    #description {
      font-family: 'Avenir', Helvetica, Arial, sans-serif;
      font-size: 15px;
      font-weight: 300;
    }

    #infowindow-content .title {
      font-weight: bold;
    }

    #infowindow-content {
      display: none;
    }

    #map #infowindow-content {
      display: inline;
    }

    .pac-card {
      margin: 10px 10px 0 0;
      border-radius: 2px 0 0 2px;
      box-sizing: border-box;
      -moz-box-sizing: border-box;
      outline: none;
      box-shadow: 0 2px 6px rgba(0, 0, 0, 0.3);
      background-color: #fff;
      font-family: 'Avenir', Helvetica, Arial, sans-serif;
    }

    #pac-container {
      padding-bottom: 12px;
      margin-right: 12px;
    }

    .pac-controls {
      display: inline-block;
      padding: 5px 11px;
    }

    .pac-controls label {
      font-family: 'Avenir', Helvetica, Arial, sans-serif;
      font-size: 13px;
      font-weight: 300;
    }

    #pac-input {
      background-color: #fff;
      font-family: 'Avenir', Helvetica, Arial, sans-serif;
      font-size: 15px;
      font-weight: 300;
      margin-left: 12px;
      padding: 0 11px 0 13px;
      text-overflow: ellipsis;
      width: 400px;
      height: 50px;
      left: 50% !important;
      margin-left: -200px;
      top: 10px !important;
      border: 4px solid rgba(0,0,0,.15) !important;
    }

    #pac-input:focus {
      border-color: #4d90fe;
    }

    #title {
      color: #fff;
      background-color: #4d90fe;
      font-size: 25px;
      font-weight: 500;
      padding: 6px 12px;
    }
    #target {
      width: 345px;
    }

    /* === Smartphones === */
    @media only screen and (min-width : 320px) and (max-width : 767px) {
      #pac-input {
        top: 65px !important;
        width: 350px !important;
        margin-left: -175px !important;
      }
    }
</style>
