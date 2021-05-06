<template>
  <section id="skills" class="light-section">
    <div class="container-fluid">
      <h1 class="section-header">{{ heading }}</h1>
      <h3>Under this category you can find all graphics and programming skills I have experience with. </h3>
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
 

      <!-- start of skill container  -->

        <div id="portfolio-container" class="row">

          <div
            data-aos="fade-right"
            data-aos-duration="1000"
            v-for="(item, index) in filteredSkills"
            :key="index"
            class="col-sm-12 col-md-3 flex-col"
          >

            <div class="portfolio-item">
              <img :src="require(`../../assets/images/skills/${item.image}`)" />
              <div class="overlay">
                
                  <div class="skills-item-content">
                    <h3>{{ item.title }}</h3>
                    <p>{{ item.description }}</p>
                  </div>
                
              </div>
            </div>
          </div>
        </div>
            
             
      <!-- end of skill container  -->
    </div>      
    <!-- end of main container  -->

  </section>
</template>

<script>
import data from "../../data/data.json";

export default {
  name: "Skills",
  props: {},

  data() {
    return {
      skillList: data.skills.skillList,
      heading: data.main.headings.skills,
      currentFilter: data.skills.defaultFilter,
    };
  },
  computed: {
    filteredSkills() {
      var skillList = data.skills.skillList;
      var filter = this.currentFilter;
      var filtered = skillList.filter(function(x) {
        return x.filter === filter;
      });
      return filtered;
    },
    filters() {
      var filterList = [];
      var skillList = data.skills.skillList;
      filterList = skillList.filter(function(x) {
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