<template>
  <div>
    <div class="container">
      <div class="row">
        <div class="col-lg-8 col-sm-6">
          <h1>Customisation</h1>
          <p>The text will reflect mobile view</p>
          <div @click="shown()" class="text">
            <b>Text</b> <span v-html="theArrow"></span>
          </div>
          <div :class="{ hideText: hidden }">
            <!-- Library for the rich text editor vue js -->
            <VueEditor v-model="content"></VueEditor>
          </div>
          <button
            type="button"
            class="btn btn-primary"
            data-toggle="button"
            aria-pressed="false"
            autocomplete="off"
            style="margin-top: 20px; background-color: #418dcb">
            <b> Publish <i class="fas fa-chevron-right"></i> </b>
          </button>
        </div>
        <div class="col-lg-4 col-sm-6">
          <div class="iphone-x">
            <i></i>
            <b></b>
            <div class="card" style="width: 90%; height: 80%">
              <div class="card-body">
                <h2>Text</h2>
                <s v-html="`${content}`"></s>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  // importing the VueEditor library
  import { VueEditor } from "vue2-editor/dist/vue2-editor.core.js"; 

  export default {
    components: { VueEditor },
    data: () => ({
      content: "",
      hidden: false,
      theArrow: '<i class="fas fa-chevron-up"></i>',
    }),
    methods: {
      shown() {
        this.hidden = !this.hidden;
        if (this.hidden) {
          this.theArrow = '<i class="fas fa-chevron-down"></i>'; //down arrow
        } else {
          this.theArrow = '<i class="fas fa-chevron-up"></i>';  //up arrow
        }
      },
    },
  };
</script>

<style lang="scss">
  @import "~vue2-editor/dist/vue2-editor.css";

  /* Importing the Quill styles*/
  @import "~quill/dist/quill.core.css";
  @import "~quill/dist/quill.bubble.css";
  @import "~quill/dist/quill.snow.css";
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
  }
  body {
    background: #f4f6fc;
    &:after {
      content: "";
      position: absolute;
      top: 0;
      right: 0;
      padding: 10px;
      background-color: #3f436b;
      color: #fff;
      opacity: 0.6;
    }
    .row {
      margin-top: 100px;
      align-items: center;
    }
  }
  .hideText {
    display: none;
  }
  .text {
    background-color: #efefef;
    padding: 15px 40px;
    margin-bottom: 20px;
    cursor: pointer;
    display: flex;
    justify-content: space-between;
  }
  .iphone-x {
    position: relative;
    margin: 40px auto;
    width: 360px;
    height: 780px;
    background-color: #afe3ff;
    border-radius: 40px;
    box-shadow: 0px 0px 0px 11px #1f1f1f, 0px 0px 0px 13px #191919,
      0px 0px 0px 20px #111;
    display: flex;
    justify-content: center;

    &:before,
    &:after {
      content: "";
      position: absolute;
      left: 50%;
      transform: translateX(-50%);
    }

    // home button indicator
    &:after {
      bottom: 7px;
      width: 140px;
      height: 4px;
      background-color: #f2f2f2;
      border-radius: 10px;
    }

    // front camera and the speaker frame
    &:before {
      top: 0px;
      width: 56%;
      height: 30px;
      background-color: #1f1f1f;
      border-radius: 0px 0px 40px 40px;
    }

    i,
    b,
    s,
    span {
      position: absolute;
      display: block;
      color: transparenbt;
    }

    // the speaker
    i {
      top: 0px;
      left: 50%;
      transform: translate(-50%, 6px);
      height: 8px;
      width: 15%;
      background-color: #101010;
      border-radius: 8px;
      box-shadow: inset 0px -3px 3px 0px rgba(256, 256, 256, 0.2);
    }

    // the camera
    b {
      left: 10%;
      top: 0px;
      transform: translate(180px, 4px);
      width: 12px;
      height: 12px;
      background-color: #101010;
      border-radius: 12px;
      box-shadow: inset 0px -3px 2px 0px rgba(256, 256, 256, 0.2);

      &:after {
        content: "";
        position: absolute;
        background-color: #2d4d76;
        width: 6px;
        height: 6px;
        top: 2px;
        left: 2px;
        top: 3px;
        left: 3px;
        display: block;
        border-radius: 4px;
        box-shadow: inset 0px -2px 2px rgba(0, 0, 0, 0.5);
      }
    }
    // text phone area
    s {
      top: 60px;
      color: black;
      text-decoration: none;
      width: 100%;
      font-size: 18px;
      font-weight: 100;
      padding-right: 25px;
      font-family:'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
    }

    // action buttons
    span {
      bottom: 50px;
      width: 40px;
      height: 40px;
      background-color: rgba(0, 0, 0, 0.3);
      border-radius: 50%;
      left: 30px;

      & + span {
        left: auto;
        right: 30px;
      }
    }
    h2 {
      text-align: center;
    }
    .card {
      align-self: center;
      border-radius: 7%;
      overflow: hidden;
    }
    button {
      margin: 20px;
    }
  }
</style>
