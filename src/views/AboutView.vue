<template>
  <div class="about">
    <div class="header">
      <h1>Welcome to SkyWatch</h1>
    </div>
    <div class="content">
      <p>
        Welcome to my first Vue application. This is a simple weather application that is fetched
        with axios from a weather API called OpenWeatherMap. Below you can find some of the
        requirements that I have used to create this application:
      </p>
      <ul>
        <li>
          <strong>Text interpolation:</strong> I used text interpolation to display data into my
          HTML.
        </li>
        <li>
          <strong>Conditional rendering:</strong> I used v-if for conditional rendering of weather
          images based on weather conditions.
        </li>
        <li>
          <strong>Events:</strong> I used @click to bind an event to the button for fetching weather
          data.
        </li>
        <li>
          <strong>Attribute interpolation:</strong> I used v-bind to bind attributes, such as :href,
          to bind links in my nav-bar.
        </li>
        <li>
          <strong>List rendering:</strong> I used v-for to render list elements for navigation
          links.
        </li>
        <li>
          <strong>v-model:</strong> I used v-model to bind input values to latitude and longitude.
        </li>
        <li>
          <strong>Single Page Application (SPA) with Vue Router:</strong> I used Vue Router to
          create an SPA with at least two pages. I have router-links for navigation and router-view
          to display components.
        </li>
        <li>
          <strong>At least one non-Vue-Router .vue component:</strong> I have created components for
          the nav-bar and for displaying weather information.
        </li>
        <li>
          <strong>At least one component receives and uses at least one prop:</strong> My nav-bar
          component receives link data as a prop and uses it to display links.
        </li>
      </ul>
    </div>
  </div>
</template>

<style>
@media (min-width: 300px) {
  .about {
    /* min-height: 100vh; */
    padding-bottom: 520px;
    padding-top: 50px;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    background-color: #f0f0f0;

  }

  .header {
    margin-bottom: 30px;
  }

  .content {
    text-align: center;
    margin-top: 30px;
    margin-left: 10px;
    margin-right: 10px;
  }

  .content ul {
    text-align: left;
    list-style-type: none;
  }

  .content ul li {
    margin-bottom: 15px;

  }
}
</style>
