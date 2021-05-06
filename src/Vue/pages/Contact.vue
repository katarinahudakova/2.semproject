<template>
  <section id="contact" class="light-section">
    <div class="container-fluid">
      <h1 class="section-header">{{ heading }}</h1>
      <div class="row">
        <!-- start of contact content  -->
        <div
          class="col-sm-12 col-md-6 flex-col"
          data-aos="fade-right"
          data-aos-duration="1000"
          style="margin: 0 auto;"
        >
          <div class="contact-content">
            <h2>STAY IN TOUCH WITH ME</h2>
            <div class="contact-info">
              <ul class="list-group list-group-flush">
                <li v-if="contact.city !==''" class="list-group-item" style= "text-transform: uppercase" >
                  <h3 class="d-inline">
                    <i class="fas fa-map-marker-alt"></i> Location:
                  </h3>
                  <br class="d-md-none" />
                  <span>&nbsp; {{ contact.city }}</span>
                </li>
                <li class="list-group-item" v-if="contact.email !==''">
                  <h3 class="d-inline">
                    <i class="fa fa-envelope"></i> Email:
                  </h3>
                  <br class="d-md-none" />
                  <a :href="'mailto:'+ contact.email">
                    <span>{{ contact.email }}</span>
                  </a>
                </li>

                <li class="list-group-item" v-if="contact.phone !==''">
                  <h3 class="d-inline">
                    <i class="fas fa-phone"></i>  Phone:
                  </h3>
                  <br class="d-md-none" />
                  
                    <span>{{ contact.phone1 }}</span>
                    <br>
                    <span style="margin-left:20%">{{ contact.phone2 }}</span>

                </li>
                <li class="list-group-item">
                  <h3 class="d-inline">
                    <i class="fas fa-user-plus"></i> Social:
                  </h3>
                  <br class="d-md-none" />

                  <div
                    v-for="(item, i) in social"
                    :key="i"
                    class="social-item social-spacing list-inline-item"
                  >
                    <a :href="item.url" :alt="item.name">
                      <i :class="'fa-lg '+item.faClass"> </i>
                    </a>
                  </div>
                </li>
                
              </ul>
            </div>
          </div>
        </div>
        <!-- end of contact content  -->

        <div
          class="col-sm-12 col-md-6 flex-col"
          data-aos="fade-right"
          data-aos-duration="1000"
          v-if="contact.form"

        >
          <h2 style="margin-top:6%" v-if="contact.formTitle !==''">{{contact.formTitle}}</h2>

          <!-- start of contact form  -->
  
          <div class="container contact-form">
            <form :action="contact.formEndPoint" method="POST" target="_blank">
              <div class="form-group">
                <div class="input-group">
                  <div class="input-group-prepend">
                    <span class="input-group-text bg-white">
                      <i class="fa fa-user"></i>&nbsp;
                    </span>
                  </div>
                  <input name="name" type="name" placeholder="Name" class="form-control border-left-0" required>
                </div>
              </div>

              <div class="form-group">
                <div class="input-group">
                  <div class="input-group-prepend">
                    <span class="input-group-text bg-white">
                      <i class="fa fa-envelope"></i>
                    </span>
                  </div>
                  <input name="email" type="email" placeholder="E-mail" class="form-control border-left-0" required>
                </div>
              </div>

              <div class="form-group">
                <textarea name="message" class="form-control" placeholder="Message" id="message" rows="5"  required></textarea>
              </div>

              <button type="submit" class="btn">
                <i class="fa fa-paper-plane"></i> 
                Send
              </button>

              <!-- Spam Prevention from 99inbound.com -->
              <div style="position: absolute; left: -5000px;">
                <input type="checkbox" name="thunderous_midnight_blue_pinstriped_video_game" value="1" tabindex="-1" autocomplete="no">
              </div>

            </form>
          </div>
          

          <!-- end of contact form  -->

        </div>
      </div>
    </div>

  </section>
</template>

<script>
import data from "../../data/data.json";

export default {
  name: "Contact",
  props: {},
  components: {},
  data() {
    return {
      contact: data.contact,
      social: data.contact.social,
      heading: data.main.headings.contact,
    };
  },

};
</script>

<style lang="scss"></style>
