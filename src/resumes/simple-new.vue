<template>
  <div id="resume2" class="resume container-fluid">
      <div class="top-row">
        <span class="person-name">
          {{person.name.first}} {{person.name.middle}} {{person.name.last}}
        </span>
        <div id="info-flex">
          <span id="email">
            <a :href='"mailto:" + person.contact.email'>
              <i class="fa fa-envelope" aria-hidden="true"></i> {{person.contact.email}}
            </a>
          </span>
          <span id="phone">
            <i class='fa fa-phone-square' aria-hidden="true"></i> {{person.contact.phone}}
          </span>
          <span v-if="person.contact.website" id="website">
            <a :href='contactLinks.website'>
              <i class="fa fa-home" aria-hidden="true"></i> {{person.contact.website}}
              </a>
          </span>
          <span v-if="person.contact.github" id="github">
                  <a :href='contactLinks.github'>
                    <i class="fa fa-github" aria-hidden="true"></i> {{person.contact.github}}
                  </a>
          </span>
      </div>
      </div>
      <div class="skills">
        <h3> <span class="section-rec col-2"></span>  <span class="col-4"> Computer Skills</span></h3> 
        <div class="skill-block big-size" v-for="skill in person.computer_skills" :key="skill.type">
          <div class="row">
            <span class="skill-type col-2" > {{skill.type}}: </span>
            <span class="skill-list col-10"> {{skill.list}} </span>
          </div>
        </div>
      </div>
      <br>
      <div class="recent_projects">
        <h3>
          <span class="section-rec col-2"></span>  <span class="col-4">  Recent Projects </span>
        </h3>
        <div class="project-block big-size" v-for="project in person.recentprojects" :key="project.techstack">
          <div class="row">
            <span class="techstack col-2">Tech Stack</span>
            <span class="techstack col-10"> {{project.tech_stack}} </span>
          </div>
          <div class="row">
            <span class="time-year col-2">{{project.year}}</span>
            <span class="col-8"><span class="product-name">{{project.product_name}}</span> <a :href="project.url">{{project.url}}</a> </span>
          </div>
          <div class="row">
            <span class="col-2"></span>
            <span class="desc col-10">
              <ul>
                <li v-for="ditem in project.description" :key="ditem"> {{ditem.d_item}} </li>
              </ul>
            </span>
          </div>
        </div>
      </div>
      <br>
      <div class="experience">
              <h3><span class="section-rec col-2"></span>  <span class="col-4">  {{ lang.experience }} </span></h3>
                  <div class="experience-block big-size" v-for="experience in person.experience" :key="experience.company">
                    <div class="row">
                      <span class="time-period col-2">{{experience.timeperiod}}</span>
                      <span class="col-10"> <span class="job-title">{{experience.position}}</span>, {{experience.company}}</span>
                    </div>
                  </div>
      </div>
      <br>
      <div class="education">
        <h3><span class="section-rec col-2"></span>  <span class="col-4"> {{ lang.education }}  </span></h3>
                  <div class="education-block big-size" v-for="education in person.education" :key="education.degree">
                    <div class="row">
                      <span class="time-period col-2">{{education.timeperiod}}</span>
                      <span class="col-10"><span class="degree">{{education.degree}}</span>, {{education.location}}</span>
                    </div>
                  </div>
      </div>
  </div>

</template>

<script>
import Vue from 'vue';
import { getVueOptions } from './options';

const name = 'simple-new';
export default Vue.component(name, getVueOptions(name));
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="less"scoped>#resume2 {

  .section-rec {
    background: #F57900;
    display: inline-flex;
    height: 10px;
    width: auto;
  }

  font-family: 'Raleway', sans-serif;
  padding-bottom: 50px;

  a,
  a:focus,
  a:hover,
  a:visited {
    text-decoration: none;
  }

  h3 {
    font-weight: 400;
  }

  .top-row {
    width: 100%;
    padding-top: 45px;
    padding-bottom: 45px;
    text-align: center;
    display: inline-flex;
    align-items: center;

    span {
      width: 100%;
      display: block;
      text-align: left;
      float: left;
      font-weight: normal;
    }

    span.person-name {
      font-size: 50px;
      padding-left: 8%;
      padding-right: 8%;
    }
  }

  .top-row #info-flex {
    font-size: 15px;
    text-align: right;
    float: right;
    a {
      color: black;
    }

    span {
      margin-right: 0px;
    }

    i {
      margin-right: 5px;
      color: #F57900;
    }

  }
  .skills {
      padding-left: 8%;
      padding-right: 8%;
      h3 {
              color: #F57900;
      }
      .skill-type{

      }
    }
  
  .experience {
    padding-left: 8%;
    padding-right: 8%;
    h3 {
              color: #F57900;
      }
  }
  .experience-block {
    .row {
      align-items: center;
    .time-period {
      font-size: 1em;
    }
    .job-title {
      font-weight: 404;
    }
    }
  }
  .education {
    padding-left: 8%;
    padding-right: 8%;
    h3 {
      color: #F57900;
    }
    .degree {
      font-weight: 404;
    }
  }
  .recent_projects{
    padding-left: 8%;
    padding-right: 8%;
    h3 {
      color: #F57900;
    }
    .product-name {
      font-weight: 404;
    }
  }

  .big-size {
    font-size: 1.1em;
  }
}


</style>
