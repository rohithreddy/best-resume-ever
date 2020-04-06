<template>
  <div id="resume2" class="resume">
      <div class="top-row">
          <span class="person-name">
            {{person.name.first}} {{person.name.middle}} {{person.name.last}}
          </span>
      <div id="info-flex">
                <span id="email"><a :href='"mailto:" + person.contact.email'>
                  <i class="fa fa-envelope" aria-hidden="true"></i> {{person.contact.email}}</a></span>
                <span id="phone"><i class='fa fa-phone-square' aria-hidden="true"></i> {{person.contact.phone}}</span>
                <span v-if="person.contact.website" id="website"><a :href='contactLinks.website'><i class="fa fa-home" aria-hidden="true"></i> {{person.contact.website}}</a></span>
                <span v-if="person.contact.github" id="github"><a :href='contactLinks.github'><i class="fa fa-github" aria-hidden="true"></i> {{person.contact.github}}</a></span>
      </div>
      </div>
      <div class="left-col">
          <div class="person-image">
              <div class="image-centerer">
                <div v-if="person.about">
            <h2>{{ lang.about }}</h2>
            <p>{{person.about}}</p>
        </div>
                  <!-- <div class="img"></div> -->
              </div>
          </div>
        <div class="skills-block">
              <h3>{{ lang.skills }}</h3>
              <div class="skills">
                      <div class="skill" v-for="skill in person.skills" :key="skill.name">
                          <span class="skill-name">{{skill.name}}</span>
              </div>
              </div>
              <span class="skills-other"> {{person.knowledge}} </span>
          </div>
          <div class="education">
              <h3>{{ lang.education }}</h3>
                  <div class="education-block" v-for="education in person.education" :key="education.degree">
                      <div class="row">
                          <span class="degree">{{education.degree}}</span>
                      </div>
                      <div class="row">
                          <span class="degree-description">{{education.description}}</span>
                      </div>
                  </div>
          </div>
          <div class="freelanceexperience">
              <h3>{{ lang.freelanceexperience }}</h3>
                  <div class="freelance-experience-block" v-for="experience in person.freelanceexperience" :key="experience.company">
                      <div class="row">
                          <span class="company"> {{experience.company}}</span>
                      </div>
                      <div class="row">
                          <span class="job-description" v-html="experience.description"> </span>
                      </div>
                  </div>
          </div>
      </div>
      <div class="right-col">
          <div class="experience">
              <h3>{{ lang.experience }}</h3>
                  <div class="experience-block" v-for="experience in person.experience" :key="experience.company">
                      <div class="row">
                          <span class="company"> {{experience.company}} -</span>
                          <span class="job-title"> {{experience.position}} </span>
                      </div>
                      <div class="row">
                          <span class="time-period"> {{experience.timeperiod}}</span>
                      </div>
                      <div class="row">
                          <span class="job-description" v-html="experience.description"> </span>
                      </div>
                  </div>
          </div>
      </div>
  </div>

</template>

<script>
import Vue from 'vue';
import { getVueOptions } from './options';

const name = 'side-bar';
export default Vue.component(name, getVueOptions(name));
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="less" scoped>
#resume2 {
  font-family:'Raleway', sans-serif;
  padding-bottom:50px;
  a, a:focus, a:hover, a:visited {
    text-decoration:none;
  }
  h3 {
    text-transform:uppercase;
    padding-top:0;
    margin-top:0;
    letter-spacing:5px;
    font-weight:400;
  }
  .top-row {
    width:100%;
    padding-top:80px;
    padding-bottom:80px;
    span {
      width:100%;
      display:block;
      text-align:left;
      font-weight:normal;
    }
    span.person-name {
      font-size:25px;
      padding-left: 8%;

      // letter-spacing:5px;
    }
    span.person-position {
      letter-spacing:5px;
    }
  }
  .top-row #info-flex {

                display:inline-table;
                // margin-top:40px;
                font-size:12px;
                text-align: right;
                position: absolute;
                right: 8%;
                top: 3%;
                a {
        color:black;
      }
                span {
                    margin-right:0px;
                }
                i {
                    margin-right:5px;
                    color: #F57900;
                }

  }
  .left-col {
    width:26%;
    float:left;
    padding-left:8%;
    padding-right:4%;
    .person-image .image-centerer {
      display:flex;
      justify-content:center;
      height:auto;
      overflow:hidden;
      .img {
        flex:none;
        background:url('../../resume/id.jpg');
        background-position:center;
        background-size:cover;
        height:250px;
        width:100%;
      }
    }
    .skills-block {
      margin-top:60px;
    }
    .education {
      margin-top:60px;
      .education-block {
        margin-bottom:10px;
        .degree {
          font-size:19px;
          text-transform:uppercase;
          margin-bottom:3px;
        }
      }
    }
    .freelanceexperience{
      margin-top: 60px;
    }
    .freelance-experience-block {
      margin-bottom:10px;
      .row:first-child {
        margin-bottom:3px;
      }
      .row .company {
        text-transform:uppercase;
        font-size:19px;
      }
      .row .job-description {
        margin-top: 10px
      }
    }
    .contact h3 {
      text-align:center;
      margin-top:20px;
    }
    .contact .contact-row {
      text-align:center;
      letter-spacing:2px;
      margin-bottom:3px;
      a {
        color:black;
      }
    }
    .contact .contact-row:first-of-type {
      margin-top:50px;
    }
    .contact .contact-row.dots {
      margin-top:20px;
      margin-bottom:15px;
      font-size:10px;
      color:rgba(153,153,153,0.6);
    }
  }
  .right-col {
    width:50%;
    float:right;
    padding-left:4%;
    padding-right:8%;
    .experience-block {
      margin-bottom:10px;
      .row:first-child {
        margin-bottom:3px;
      }
      .row .company {
        text-transform:uppercase;
        font-size:19px;
      }
      .row .job-title {
        font-size:19px;
      }
    }
    .skills-block {
      margin-top:50px;
      position:relative;
      .skills {
        margin-bottom:10px;
        margin-bottom:20px;
        position:relative;
        margin-left:auto;
        margin-right:auto;
        display:inline-block;
        .skill {
          width:80px;
          height:80px;
          border-radius:50%;
          position:relative;
          border:#333333 1px solid;
          margin:3px;
          float:left;
          font-size:13px;
          .skill-name {
            text-align:center;
            position:absolute;
            top:50%;
            transform:translateY(-50%);
            width:100%;
          }
        }
        .skills-other {
          display:inline-block;
          width:100%;
          margin-top:20px;
        }
        // #info-flex {
        //         display:flex;
        //         margin-top:20px;
        //         font-size:14px;

        //         span {
        //             margin-right:25px;
        //         }
        //         i {
        //             margin-right:5px;
        //         }
        //     }
      }
    }
  }
}
</style>
