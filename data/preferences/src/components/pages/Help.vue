<template>
  <div class="row help-page">

    <div class="col-4 item" v-for="item in items">

      <div @click="openUrlInBrowser(item.url)">
        <div class="outer-circle">
          <div class="inner-circle">
            <i :class="[item.icon, 'fa', 'fa-icon']"></i>
          </div>
        </div>
        <div class="label">{{ item.label }}</div>
      </div>

      <div class="text">{{ item.text }}</div>
    </div>

  </div>
</template>

<script>
import jsonp from '@/api'

export default {
  name: 'help',
  data () {
    return {
      items: [
        {
          icon: 'fa-github',
          label: 'Troubleshooting',
          text: 'Report a bug or ask a question on Github',
          url: 'https://github.com/Ulauncher/Ulauncher/issues'
        },
        {
          icon: 'fa-envelope',
          label: 'Email Us',
          text: "Just in case you don't want to open a Github issue for some reason, you can always email us",
          url: 'mailto:ulauncher.app@gmail.com'
        },
        {
          icon: 'fa-twitter',
          label: 'Follow on Twitter',
          text: 'Follow UlauncherApp on Twitter to get the latest updates and news',
          url: 'https://twitter.com/UlauncherApp'
        }
      ]
    }
  },
  methods: {
    openUrlInBrowser (url) {
      jsonp('prefs://open/web-url', {url: url})
    }
  }
}
</script>

<style lang="scss" scoped>
$mainGrey: #e0e0e0;
$steelBlue: #4675ab;

.help-page {
  box-sizing: border-box;
  padding: 40px;
  padding-top: 160px;
}

.item {
  cursor: pointer;

  .outer-circle {
    display: block;
    width: 94px;
    height: 94px;
    background: $mainGrey;
    border-radius: 50%;
    text-align: center;
    margin: 0 auto;
  }

  .inner-circle {
    margin-top: 7px;
    display: inline-block;
    width: 80px;
    height: 80px;
    border: 1px solid #ccc;
    border-radius: 50%;
    text-align: center;
    background: #fff;
    color: $mainGrey;

    .fa-icon {
      margin-top: 10px;
      color: $mainGrey;
      font-size: 54px;
    }
  }

  .label {
    text-transform: uppercase;
    padding: 20px 0 12px 0;
    font-size: 0.9em;
    text-align: center;
    cursor: pointer;
  }

  .text {
    color: #a7a7a7;
    text-align: center;
    font-size: 0.9em;
    visibility: hidden;
  }

  &:hover {
    .outer-circle {
      background: $steelBlue;
      .inner-circle {
        .fa-icon {
          color: $steelBlue;
        }
      }
    }
    .text {
      visibility: visible;
    }
  }
}
</style>
