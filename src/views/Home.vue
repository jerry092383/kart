<template lang="pug">
.container-fluid
  .h2
    .my-3 總隊數：{{ data.length }}

  div(v-for="(item, key) in data", :key="key")
    h3 {{ item.team_name }}
    .row
      .col-sm-12.col-md-6.col-lg-4.mb-3(
        v-for="(player, key) in item.players",
        :key="key"
      )
        .card
          img(:src="player.image_path", width="100%", height="300px")
          h4.mt-2 {{ player.game_name }} ({{ player.nick_name }}) {{ player.position_type === 2 ? '[ 候補 ]' : '' }}
</template>

<script lang="ts">
import Axios from 'axios'
import { Component, Vue } from 'vue-property-decorator'

@Component
export default class Home extends Vue {
  protected data: any[] = []

  protected created () {
    this.getKartData();
  }

  protected getKartData() {
    Axios.get(
      'https://cors-anywhere.herokuapp.com/http://dc-cs-xmas-frontend-prod-f271a7c387ea79e8.elb.ap-northeast-1.amazonaws.com/api/teams'
    ).then((res) => {
      this.data = res.data
    })
  }
}
</script>
