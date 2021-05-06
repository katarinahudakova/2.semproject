<template>
  <section id="portfolio" class="dark-section">
    <div class="container-fluid">
      <h1 class="section-header">{{ heading }}</h1>

      <!-- start of filters  -->

      <div class="row filters">
        <ul class="list-inline mx-auto">
          <li
            v-for="item in filters"
            :key="item.title"
            class="list-inline-item filter"
          >
            <a
              class="nav-item"
              :class="item.filter === currentFilter ? 'active' : null"
              :data-filter="item.filter"
              @click="setFilter"
              >{{ item.filter }}</a
            >
          </li>
        </ul>
      </div>
      
      <!-- end of filters  -->


      <!-- start of project container -->
      <div 
      id="portfolio-container" class="row"
      >
       <div
         data-aos="fade-right"
         data-aos-duration="1000"
         v-for="(item, index) in filteredProjects"
         :key="index"
         class="col-sm-12 col-md-4 flex-col"
       >

          <div
          v-if="item.filter === 'websites'"
          class="portfolio-item"
          >
            <video style="max-width:100%; max-height:auto display:block" autoplay loop muted>
                <source :src="require(`../../assets/images/portfolio/${item.video}`)" type="video/mp4">
            </video>
            <div class="overlay">
                <div class="portfolio-item-content">
                  <h3>{{ item.title }}</h3>
                  <p>{{ item.description }}</p>
                </div> 
            </div>
          </div>

          <div 
          v-else
          class="portfolio-item"
          >
            <img :src="require(`../../assets/images/portfolio/${item.image}`)" />
            <div class="overlay">
                <div class="portfolio-item-content">
                  <h3>{{ item.title }}</h3>
                  <p>{{ item.description }}</p>
                </div>
            </div>
          </div>

        </div>
      </div>

      <!-- end of project container -->

    </div>
  <!-- end of main container  -->
  
  </section>
</template>

<script>
import data from "../../data/data.json";

export default {
  name: "portfolio",
  props: {},
  
  data() {
    return {
      projects: data.portfolio.projects,
      heading: data.main.headings.projects,
      currentFilter: data.portfolio.defaultFilter,
    };
  },
  computed: {
    filteredProjects() {
      var projects = data.portfolio.projects;
      var filter = this.currentFilter;
      var filtered = projects.filter(function(x) {
        return x.filter === filter;
      });
      return filtered;
    },
    filters() {
      var filterList = [];
      var projects = data.portfolio.projects;
      filterList = projects.filter(function(x) {
        if (!filterList.includes(x.filter)) {
          filterList.push(x.filter);
          return x.filter;
        }
      });
      return filterList;
    },
  },
  methods: {
    setFilter(event) {
      this.currentFilter = event.target.dataset.filter;
    },
  },
};
</script>

<style lang="scss"></style>
