<template>
  <section id="about" class="dark-section">
    <div class="container-fluid">
      <h1 class="section-header">{{ heading }}</h1>
      <div class="row">
        <div
          class="col-sm-12 col-md-4 flex-col"
          data-aos="fade-right"
          data-aos-duration="1000"
        >
          <img
            class="profile-pic"
            src="../../assets/images/illustration.png"
            alt="profile picture"
          />
        </div>
        <div
          class="col-sm-12 col-md-4 flex-col"
          data-aos="fade-right"
          data-aos-duration="1000"
        >
          <p id="about-content">
            <span id="greeting">I'm {{ name }}! </span>
            <span id="bio" v-html="about.bio"></span> &#128522;
          </p>
        </div>

        <div
          class="col-sm-12 col-md-4 flex-col"
          data-aos="fade-right"
          data-aos-duration="1000"
        >

          <div>
            <a href="https://drive.google.com/file/d/19qszmLxG6GC1zHefjhDP1DHQjKIQyDh1/view?usp=sharing" title="CV Katarina Hudakova" target="_blank">
              <img
                class="cv-pic"
                src="../../assets/images/CV.png"
                alt="CV picture"
              />
            </a>
          </div>

        </div>
      </div>

      <div class="row">
        <div
          class="col-sm-12 col-md-12 flex-col"
          data-aos="fade-right"
          data-aos-duration="1000"
        >
          <video style="max-width:50%; max-height:auto" controls>
            <source src="" type="video/mp4">
          </video>

        </div>
      </div>
    </div>

  </section>
</template>

<script>
import data from "../../data/data.json";

export default {
  name: "About",
  props: {},
  data() {
    return {
      about: data.about,
      name: data.main.name.first,
      heading: data.main.headings.about,
    };
  },
};
</script>

<style lang="scss"></style>