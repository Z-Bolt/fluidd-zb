<template>
  <v-list dense>
    <v-subheader>{{ $t('app.general.label.layout') }}</v-subheader>

    <v-list-item @click.prevent="layoutMode = !layoutMode">
      <v-list-item-icon>
        <v-icon>$apps</v-icon>
      </v-list-item-icon>

      <v-list-item-content>
        <v-list-item-title class="text-wrap">
          {{ $t('app.general.btn.adjust_layout') }}
        </v-list-item-title>
      </v-list-item-content>
    </v-list-item>
  </v-list>
</template>

<script lang="ts">
import { Component, Mixins } from 'vue-property-decorator'
import StateMixin from '@/mixins/state'

@Component({})
export default class SystemLayout extends Mixins(StateMixin) {
  get layoutMode (): boolean {
    return this.$store.state.config.layoutMode
  }

  set layoutMode (val: boolean) {
    this.$store.commit('config/setLayoutMode', val)
    this.close()
  }

  close () {
    this.$emit('click')
  }
}
</script>
