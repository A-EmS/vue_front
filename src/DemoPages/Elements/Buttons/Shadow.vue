<template>
  <div>
    <page-title :heading=heading :subheading=subheading :icon=icon></page-title>
    <tabs
      :tabs="tabs"
      :currentTab="currentTab"
      :wrapper-class="'body-tabs shadow-tabs'"
      :tab-class="'tab-item'"
      :tab-active-class="'tab-item-active'"
      :line-class="'tab-item-line'"
      @onClick="handleClick"
    />
    <div class="content">
      <div v-if="currentTab === 'tab1'">
        <b-row>
          <b-col lg="6">
            <div class="main-card mb-3 card">
              <div class="card-body">
                <h5 class="card-title">Solid</h5>
                <template v-for="variant in ['primary','secondary','success','info','warning','danger','focus','alternate','light','dark','link']">
                  <b-button class="mr-2 mb-2 btn-shadow" :variant="variant">
                    {{variant}}
                  </b-button>
                </template>
              </div>
            </div>
          </b-col>
          <b-col lg="6">
            <div class="main-card mb-3 card">
              <div class="card-body">
                <h5 class="card-title">Color Transition</h5>
                <template v-for="variant in ['outline-primary','outline-secondary','outline-success','outline-info','outline-warning','outline-danger','outline-focus','outline-alternate','outline-light','outline-dark','outline-link']">
                  <b-button class="mr-2 mb-2 btn-shadow btn-transition" :variant="variant">
                    {{variant}}
                  </b-button>
                </template>
              </div>
            </div>
          </b-col>
          <b-col lg="6">
            <div class="main-card mb-3 card">
              <div class="card-body">
                <h5 class="card-title">Color Transition no Borders</h5>
                <template v-for="variant in ['outline-primary','outline-secondary','outline-success','outline-info','outline-warning','outline-danger','outline-focus','outline-alternate','outline-light','outline-dark','outline-link']">
                  <b-button class="mr-2 mb-2 btn-shadow border-0 btn-transition" :variant="variant">
                    {{variant}}
                  </b-button>
                </template>
              </div>
            </div>
          </b-col>
          <b-col lg="6">
            <div class="main-card mb-3 card">
              <div class="card-body">
                <h5 class="card-title">Hover Shine</h5>
                <template v-for="variant in ['primary','secondary','success','info','warning','danger','focus','alternate','light','dark','link']">
                  <b-button class="mr-2 mb-2 btn-shadow btn-hover-shine btn-transition" :variant="variant">
                    {{variant}}
                  </b-button>
                </template>
              </div>
            </div>
          </b-col>
          <b-col lg="6">
            <div class="main-card mb-3 card">
              <div class="card-body">
                <h5 class="card-title">Active State</h5>
                <template v-for="variant in ['primary','secondary','success','info','warning','danger','focus','alternate','light','dark','link']">
                  <b-button :pressed="true" class="mr-2 mb-2 btn-shadow" :variant="variant">
                    {{variant}}
                  </b-button>
                </template>
              </div>
            </div>
          </b-col>
          <b-col lg="6">
            <div class="main-card mb-3 card">
              <div class="card-body">
                <h5 class="card-title">Disabled</h5>
                <template v-for="variant in ['primary','secondary','success','info','warning','danger','focus','alternate','light','dark','link']">
                  <b-button disabled class="mr-2 mb-2 btn-shadow" :variant="variant">
                    {{variant}}
                  </b-button>
                </template>
              </div>
            </div>
          </b-col>
          <b-col lg="6">
            <div class="main-card mb-3 card">
              <div class="card-body">
                <h5 class="card-title">Block Level</h5>
                <template v-for="size in ['sm','','lg']">
                  <b-button block class="mr-2 mb-2 btn-shadow" variant="primary" :size="size">
                    Block {{size}}
                  </b-button>
                </template>
              </div>
            </div>
          </b-col>
          <b-col lg="6">
            <div class="main-card mb-3 card">
              <div class="card-body">
                <h5 class="card-title">Wider</h5>
                <template v-for="size in ['sm','','lg']">
                  <b-button class="btn-wide mr-2 mb-2 btn-shadow" variant="primary" :size="size">
                    Wider {{size}}
                  </b-button>
                </template>
              </div>
            </div>
            <div class="main-card mb-3 card">
              <div class="card-body">
                <h5 class="card-title">Sizing</h5>
                <template v-for="size in ['sm','','lg']">
                  <b-button class="mr-2 mb-2 btn-shadow" variant="primary" :size="size">
                    Button {{size}}
                  </b-button>
                </template>
              </div>
            </div>
          </b-col>
        </b-row>
        <div class="main-card mb-3 card">
          <div class="card-body">
            <h5 class="card-title">Loading Buttons</h5>
            <b-row class="text-center">
              <b-col md="3" v-for="(button, index) in buttons" :key="index">
                <vue-ladda button-class="ladda-button btn-shadow btn btn-primary mb-2 mr-2"
                           :loading="button.loading"
                           :data-style="button.dataStyle"
                           :progress="button.progress"
                           @click="submit(button)">
                  {{button.dataStyle}}
                </vue-ladda>
              </b-col>
            </b-row>
          </div>
        </div>
      </div>
      <div v-if="currentTab === 'tab2'">
        <b-row>
          <b-col lg="6">
            <div class="main-card mb-3 card">
              <div class="card-body">
                <h5 class="card-title">Color States</h5>
                <template v-for="variant in ['outline-primary','outline-secondary','outline-success','outline-info','outline-warning','outline-danger','outline-focus','outline-alternate','outline-light','outline-dark','outline-link']">
                  <b-button class="mr-2 mb-2 btn-shadow btn-transition" :variant="variant">
                    {{variant}}
                  </b-button>
                </template>
              </div>
            </div>
          </b-col>
          <b-col lg="6">
            <div class="main-card mb-3 card">
              <div class="card-body">
                <h5 class="card-title">Active State</h5>
                <template v-for="variant in ['outline-primary','outline-secondary','outline-success','outline-info','outline-warning','outline-danger','outline-focus','outline-alternate','outline-light','outline-dark','outline-link']">
                  <b-button :pressed="true" class="mr-2 mb-2 btn-shadow" :variant="variant">
                    {{variant}}
                  </b-button>
                </template>
              </div>
            </div>
          </b-col>
          <b-col lg="6">
            <div class="main-card mb-3 card">
              <div class="card-body">
                <h5 class="card-title">Disabled</h5>
                <template v-for="variant in ['outline-primary','outline-secondary','outline-success','outline-info','outline-warning','outline-danger','outline-focus','outline-alternate','outline-light','outline-dark','outline-link']">
                  <b-button disabled class="mr-2 mb-2 btn-shadow" :variant="variant">
                    {{variant}}
                  </b-button>
                </template>
              </div>
            </div>
          </b-col>
          <b-col lg="6">
            <div class="main-card mb-3 card">
              <div class="card-body">
                <h5 class="card-title">Block Level</h5>
                <template v-for="size in ['sm','','lg']">
                  <b-button block class="mr-2 mb-2 btn-shadow" variant="outline-primary" :size="size">
                    Block {{size}}
                  </b-button>
                </template>
              </div>
            </div>
          </b-col>
          <b-col lg="6">
            <div class="main-card mb-3 card">
              <div class="card-body">
                <h5 class="card-title">Wider</h5>
                <template v-for="size in ['sm','','lg']">
                  <b-button class="btn-wide mr-2 mb-2 btn-shadow" variant="outline-primary" :size="size">
                    Wider {{size}}
                  </b-button>
                </template>
              </div>
            </div>
          </b-col>
          <b-col lg="6">
            <div class="main-card mb-3 card">
              <div class="card-body">
                <h5 class="card-title">Sizing</h5>
                <template v-for="size in ['sm','','lg']">
                  <b-button class="mr-2 mb-2 btn-shadow" variant="outline-primary" :size="size">
                    Button {{size}}
                  </b-button>
                </template>
              </div>
            </div>
          </b-col>
        </b-row>
        <div class="main-card mb-3 card">
          <div class="card-body">
            <h5 class="card-title">Loading Buttons</h5>
            <b-row class="text-center">
              <b-col md="3" v-for="(button, index) in buttons" :key="index">
                <vue-ladda button-class="ladda-button btn-shadow btn btn-outline-primary mb-2 mr-2"
                           :loading="button.loading"
                           :data-style="button.dataStyle"
                           :progress="button.progress"
                           @click="submit(button)">
                  {{button.dataStyle}}
                </vue-ladda>
              </b-col>
            </b-row>
          </div>
        </div>
      </div>
      <div v-if="currentTab === 'tab3'">
        <b-row>
          <b-col lg="6">
            <div class="main-card mb-3 card">
              <div class="card-body">
                <h5 class="card-title">Color States</h5>
                <template v-for="variant in ['outline-primary','outline-secondary','outline-success','outline-info','outline-warning','outline-danger','outline-focus','outline-alternate','outline-light','outline-dark','outline-link']">
                  <b-button class="mr-2 mb-2 btn-shadow btn-outline-2x btn-transition" :variant="variant">
                    {{variant}}
                  </b-button>
                </template>
              </div>
            </div>
          </b-col>
          <b-col lg="6">
            <div class="main-card mb-3 card">
              <div class="card-body">
                <h5 class="card-title">Active State</h5>
                <template v-for="variant in ['outline-primary','outline-secondary','outline-success','outline-info','outline-warning','outline-danger','outline-focus','outline-alternate','outline-light','outline-dark','outline-link']">
                  <b-button :pressed="true" class="mr-2 mb-2 btn-shadow btn-outline-2x" :variant="variant">
                    {{variant}}
                  </b-button>
                </template>
              </div>
            </div>
          </b-col>
          <b-col lg="6">
            <div class="main-card mb-3 card">
              <div class="card-body">
                <h5 class="card-title">Disabled</h5>
                <template v-for="variant in ['outline-primary','outline-secondary','outline-success','outline-info','outline-warning','outline-danger','outline-focus','outline-alternate','outline-light','outline-dark','outline-link']">
                  <b-button disabled class="mr-2 mb-2 btn-shadow btn-outline-2x" :variant="variant">
                    {{variant}}
                  </b-button>
                </template>
              </div>
            </div>
          </b-col>
          <b-col lg="6">
            <div class="main-card mb-3 card">
              <div class="card-body">
                <h5 class="card-title">Block Level</h5>
                <template v-for="size in ['sm','','lg']">
                  <b-button block class="mr-2 mb-2 btn-shadow btn-outline-2x" variant="outline-primary" :size="size">
                    Block {{size}}
                  </b-button>
                </template>
              </div>
            </div>
          </b-col>
          <b-col lg="6">
            <div class="main-card mb-3 card">
              <div class="card-body">
                <h5 class="card-title">Wider</h5>
                <template v-for="size in ['sm','','lg']">
                  <b-button class="btn-wide mr-2 mb-2 btn-shadow btn-outline-2x" variant="outline-primary" :size="size">
                    Wider {{size}}
                  </b-button>
                </template>
              </div>
            </div>
          </b-col>
          <b-col lg="6">
            <div class="main-card mb-3 card">
              <div class="card-body">
                <h5 class="card-title">Sizing</h5>
                <template v-for="size in ['sm','','lg']">
                  <b-button class="mr-2 mb-2 btn-shadow btn-outline-2x" variant="outline-primary" :size="size">
                    Button {{size}}
                  </b-button>
                </template>
              </div>
            </div>
          </b-col>
        </b-row>
        <div class="main-card mb-3 card">
          <div class="card-body">
            <h5 class="card-title">Loading Buttons</h5>
            <b-row class="text-center">
              <b-col md="3" v-for="(button, index) in buttons" :key="index">
                <vue-ladda button-class="ladda-button btn-shadow btn-outline-2x btn btn-outline-primary mb-2 mr-2"
                           :loading="button.loading"
                           :data-style="button.dataStyle"
                           :progress="button.progress"
                           @click="submit(button)">
                  {{button.dataStyle}}
                </vue-ladda>
              </b-col>
            </b-row>
          </div>
        </div>
      </div>
      <div v-if="currentTab === 'tab4'">
        <b-row>
          <b-col lg="6">
            <div class="main-card mb-3 card">
              <div class="card-body">
                <h5 class="card-title">Color States</h5>
                <template v-for="variant in ['outline-primary','outline-secondary','outline-success','outline-info','outline-warning','outline-danger','outline-focus','outline-alternate','outline-light','outline-dark','outline-link']">
                  <b-button class="mr-2 mb-2 btn-shadow btn-dashed btn-transition" :variant="variant">
                    {{variant}}
                  </b-button>
                </template>
              </div>
            </div>
          </b-col>
          <b-col lg="6">
            <div class="main-card mb-3 card">
              <div class="card-body">
                <h5 class="card-title">Active State</h5>
                <template v-for="variant in ['outline-primary','outline-secondary','outline-success','outline-info','outline-warning','outline-danger','outline-focus','outline-alternate','outline-light','outline-dark','outline-link']">
                  <b-button :pressed="true" class="mr-2 mb-2 btn-shadow btn-dashed" :variant="variant">
                    {{variant}}
                  </b-button>
                </template>
              </div>
            </div>
          </b-col>
          <b-col lg="6">
            <div class="main-card mb-3 card">
              <div class="card-body">
                <h5 class="card-title">Disabled</h5>
                <template v-for="variant in ['outline-primary','outline-secondary','outline-success','outline-info','outline-warning','outline-danger','outline-focus','outline-alternate','outline-light','outline-dark','outline-link']">
                  <b-button disabled class="mr-2 mb-2 btn-shadow btn-dashed" :variant="variant">
                    {{variant}}
                  </b-button>
                </template>
              </div>
            </div>
          </b-col>
          <b-col lg="6">
            <div class="main-card mb-3 card">
              <div class="card-body">
                <h5 class="card-title">Block Level</h5>
                <template v-for="size in ['sm','','lg']">
                  <b-button block class="mr-2 mb-2 btn-shadow btn-dashed" variant="outline-primary" :size="size">
                    Block {{size}}
                  </b-button>
                </template>
              </div>
            </div>
          </b-col>
          <b-col lg="6">
            <div class="main-card mb-3 card">
              <div class="card-body">
                <h5 class="card-title">Wider</h5>
                <template v-for="size in ['sm','','lg']">
                  <b-button class="btn-wide mr-2 mb-2 btn-shadow btn-dashed" variant="outline-primary" :size="size">
                    Wider {{size}}
                  </b-button>
                </template>
              </div>
            </div>
          </b-col>
          <b-col lg="6">
            <div class="main-card mb-3 card">
              <div class="card-body">
                <h5 class="card-title">Sizing</h5>
                <template v-for="size in ['sm','','lg']">
                  <b-button class="mr-2 mb-2 btn-shadow btn-dashed" variant="outline-primary" :size="size">
                    Button {{size}}
                  </b-button>
                </template>
              </div>
            </div>
          </b-col>
        </b-row>
        <div class="main-card mb-3 card">
          <div class="card-body">
            <h5 class="card-title">Loading Buttons</h5>
            <b-row class="text-center">
              <b-col md="3" v-for="(button, index) in buttons" :key="index">
                <vue-ladda button-class="ladda-button btn-shadow btn-dashed btn btn-outline-primary mb-2 mr-2"
                           :loading="button.loading"
                           :data-style="button.dataStyle"
                           :progress="button.progress"
                           @click="submit(button)">
                  {{button.dataStyle}}
                </vue-ladda>
              </b-col>
            </b-row>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

  import PageTitle from "../../../Layout/Components/PageTitle.vue";
  import Tabs from 'vue-tabs-with-active-line';
  import VueLadda from '../../../assets/components/ladda-loading/src/vue-ladda'

  const TABS = [{
    title: 'Solid',
    value: 'tab1',
  }, {
    title: 'Outline',
    value: 'tab2',
  }, {
    title: 'Outline 2x',
    value: 'tab3',
  }, {
    title: 'Dashed',
    value: 'tab4',
  }];

  export default {
    components: {
      PageTitle,
      Tabs,
      'vue-ladda': VueLadda,
    },
    data: () => ({
      heading: 'Shadow Buttons',
      subheading: 'These buttons are examples of buttons with drop shadows attached.',
      icon: 'pe-7s-monitor icon-gradient bg-malibu-beach',

      tabs: TABS,
      currentTab: 'tab1',

      buttons: [
        {
          loading: false,
          'dataStyle': 'expand-left',
          progress: 0,
        },
        {
          loading: false,
          'dataStyle': 'expand-right',
          progress: 0
        },
        {
          loading: false,
          'dataStyle': 'zoom-in',
          progress: 0
        },
        {
          loading: false,
          'dataStyle': 'zoom-out',
          progress: 0
        },
        {
          loading: false,
          'dataStyle': 'slide-left',
          progress: 0
        },
        {
          loading: false,
          'dataStyle': 'slide-right',
          progress: 0
        },
        {
          loading: false,
          'dataStyle': 'slide-up',
          progress: 0
        },
        {
          loading: false,
          'dataStyle': 'slide-down',
          progress: 0
        },
        {
          loading: false,
          'dataStyle': 'expand-up',
          progress: 0
        },
        {
          loading: false,
          'dataStyle': 'expand-down',
          progress: 0
        },
      ],
      selected: [], // Must be an array reference!
      options: [
        {text: 'Orange', value: 'orange'},
        {text: 'Apple', value: 'apple'},
        {text: 'Pineapple', value: 'pineapple'},
        {text: 'Grape', value: 'grape'}
      ],
      selected2: 'radio1',
      options2: [
        {text: 'Radio 1', value: 'radio1'},
        {text: 'Radio 3', value: 'radio2'},
        {text: 'Radio 3 (disabled)', value: 'radio3', disabled: true},
        {text: 'Radio 4', value: 'radio4'}
      ]
    }),

    methods: {
      handleClick(newTab) {
        this.currentTab = newTab;
      },
      submit: function (button) {
        const duration = 2000;
        button.loading = true;
        updateButtonProgress(duration, button);
        setTimeout(function () {
          button.loading = false;
        }, duration);
      }
    }
  }


  function updateButtonProgress(duration, button) {
    var start = null;

    function update(timestamp) {
      var delta, progress;
      if (!start) start = timestamp;
      delta = timestamp - start;
      progress = delta / duration;
      if (progress >= 1 || progress < 0) return;
      button.progress = progress;
      window.requestAnimationFrame(update);
    }

    window.requestAnimationFrame(update);
  }
</script>
