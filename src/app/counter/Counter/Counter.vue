<template>
  <div :class="$style.counter">
    <vue-grid>
      <vue-grid-row>
        <vue-grid-item fill>
          <h1>{{ $t('App.nav.counter' /* Counter */) }}</h1>
        </vue-grid-item>

        <vue-grid-item fill>
          <vue-button @click='increment' accent>Increment +1</vue-button>
          <vue-button @click='decrement' primary>Decrement -1</vue-button>
          <h3>Count is {{ count }}</h3>
        </vue-grid-item>
      </vue-grid-row>
    </vue-grid>
  </div>
</template>

<script lang="ts">
  import { mapGetters, mapActions } from 'vuex';
  import VueGrid                    from '../../shared/components/VueGrid/VueGrid';
  import VueGridItem                from '../../shared/components/VueGridItem/VueGridItem';
  import VueButton                  from '../../shared/components/VueButton/VueButton';
  import VueGridRow                 from '../../shared/components/VueGridRow/VueGridRow';

  export default {
    metaInfo:   {
      title: 'Counter',
    },
    components: {
      VueGrid,
      VueGridItem,
      VueButton,
      VueGridRow,
    },
    methods:    {
      ...mapActions([
                      'increment',
                      'decrement',
                    ]),
    },
    computed:   {
      ...mapGetters({
                      count: 'getCount',
                    }),
    },
  };
</script>

<style lang="scss" module>
  @import "../../shared/styles";

  .counter {
    margin-top: $nav-bar-height;
    min-height: 500px;
  }
</style>
