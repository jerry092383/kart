<template lang="pug">
  h1 qwe
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'
import Axios from 'axios'

@Component
export default class About extends Vue {
  protected created () {
    this.getGameInfo()
  }

  protected getGameInfo () {
    Axios.get('https://cors-anywhere.herokuapp.com/http://dc-cs-xmas-frontend-prod-f271a7c387ea79e8.elb.ap-northeast-1.amazonaws.com/api/game')
      .then(res => {
        console.log('res :>> ', res)
      })
  }
}
</script>
