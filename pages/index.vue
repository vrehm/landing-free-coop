<template>
  <div
    id="app"
    class="container mx-auto flex flex-wrap justify-center items-center"
  >
    <!-- <div class="w-full">
      <h1>vue-progress-path</h1>

      <pre>{{ installCode }}</pre>
      <pre>{{ usageCode }}</pre>
    </div> -->

    <div class="settings w-full">
      <div>
        <input v-model="progressModel" type="range" min="-100" max="100" />
        <button @click="progress = 0">reset</button>
        <span>progress {{ progressDisplay }}</span>
      </div>

      <div>
        <label>
          <input v-model="indeterminate" type="checkbox" />
          indeterminate
        </label>
      </div>

      <div>
        <label>
          <input v-model="counterClockwise" type="checkbox" />
          counter clockwise
        </label>
      </div>

      <div>
        <label>
          <input v-model="hideBackground" type="checkbox" />
          hide background
        </label>
      </div>
    </div>

    <div class="w-full flex justify-center">
      <!-- <loading-progress
          :progress="progress"
          :indeterminate="indeterminate"
          :counter-clockwise="counterClockwise"
          :hide-background="hideBackground"
          size="64"
          rotate
          fill-duration="2"
          rotation-duration="1"
        />

        <loading-progress
          :progress="progress"
          :indeterminate="indeterminate"
          :counter-clockwise="counterClockwise"
          :hide-background="hideBackground"
          shape="semicircle"
          size="64"
        />

        <loading-progress
          :progress="progress"
          :indeterminate="indeterminate"
          :counter-clockwise="counterClockwise"
          :hide-background="hideBackground"
          shape="line"
          size="200"
          width="200"
          height="6"
        />

        <loading-progress
          :progress="progress"
          :indeterminate="indeterminate"
          :counter-clockwise="counterClockwise"
          :hide-background="hideBackground"
          shape="square"
          size="64"
          fill-duration="2"
        /> -->

      <loading-progress
        :progress="progress"
        :indeterminate="indeterminate"
        :counter-clockwise="counterClockwise"
        :hide-background="hideBackground"
        shape="M 100 300 Q 150 50 200 300 Q 250 550 300 300 Q 350 50 400 300 Q 450 550 500 300 Q 550 50 600 300 Q 650 550 700 300"
        size="750"
        fill-duration="2"
      />

      <!-- <loading-progress
          :progress="progress"
          :indeterminate="indeterminate"
          :counter-clockwise="counterClockwise"
          :hide-background="hideBackground"
          shape="M50,3l12,36h38l-30,22l11,36l-31-21l-31,21l11-36l-30-22h38z"
          size="100"
          fill-duration="2"
        /> -->
    </div>
  </div>
</template>

<script>
const installCode = `npm i -S vue-progress-path
yarn add vue-progress-path`

const usageCode = `import Vue from 'vue'
import VueProgress from 'vue-progress-path'
Vue.use(VueProgress)`

export default {
  data() {
    return {
      indeterminate: false,
      progress: 0,
      counterClockwise: false,
      hideBackground: false,
      installCode,
      usageCode
    }
  },

  computed: {
    progressModel: {
      get() {
        return this.progress * 100
      },
      set(value) {
        this.progress = value / 100
      }
    },

    progressDisplay() {
      return `${Math.round(this.progress * 100)}%`
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}

h1,
h2 {
  font-weight: normal;
}

a {
  color: #42b983;
}

pre {
  background: #eee;
  padding: 12px;
}

h1,
h2,
pre,
.view,
.settings {
  margin: 32px;
}

.view {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
}

.settings {
  padding-top: 32px;
  border-top: solid 1px #eee;
}

input[type='range'] {
  width: calc(100vw - 300px);
}
</style>
