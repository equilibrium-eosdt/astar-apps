<template>
  <div class="header">
    <div class="header-left">
      <div v-if="title">{{ title }}</div>
      <div v-else>
        <slot name="left"></slot>
      </div>
    </div>
    <div class="header-right">
      <slot></slot>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, toRefs } from 'vue';

export default defineComponent({
  name: 'HeaderComp',
  props: {
    title: {
      type: String,
      default: '',
    },
  },
  setup(props) {
    return {
      ...toRefs(props),
    };
  },
});
</script>

<style lang="scss" scoped>
@import 'src/css/quasar.variables.scss';

.header {
  overflow: hidden;
  display: flex;
  justify-content: space-between;
  height: 6rem;
  padding: 40px 40px 25px 40px;
  background: rgba(247, 247, 248, 0.8);
  mix-blend-mode: normal;
  backdrop-filter: blur(200px);
  border-bottom: 1px solid $object-light;
  @media (min-width: $lg) {
    padding-left: 28px;
    padding-right: 28px;
  }
}

.header-left {
  display: flex;
  height: 100%;
  align-items: center;
  font-weight: 590;
  font-size: 1.625rem;
  padding: 0.75rem;
  color: $gray-5-selected;
}

.header-right {
  display: flex;
  height: 100%;
  align-items: center;
  padding: 0.75rem;
}

.body--dark {
  .header {
    background: rgba(25, 29, 31, 0.8) !important;
    border-bottom: 1px solid $gray-5;
  }
  .header-left {
    color: $gray-1;
  }
}

@media screen and (max-width: $lg) {
  .header {
    height: 4rem;
    padding-top: 36px;
    padding-left: 20px;
    padding-right: 16px;
    background: $gray-1;
    border-bottom: 0px !important;
  }

  .header-left {
    padding: 0rem;
  }

  .header-right {
    padding: 0rem;
  }

  .body--dark {
    .header {
      background: $gray-6 !important;
    }
  }
}
</style>
