<template>
  <div class="home-license-filter margin-top-xl">
    <span>I want something I can</span>

    <template v-for="(licenseType, index) in licenseTypes" >
      <label class="checkbox margin-right-big" :for="licenseType.code" :key="index">
        <input :id="licenseType.code"
              type="checkbox"
              :checked="licenseType.checked"
              name="lt"
              :value="licenseType.code"
              @input="onFilterChanged(licenseType.code)" />
        {{ licenseType.name }}
      </label>
    </template>
  </div>
</template>

<script>
import { TOGGLE_FILTER } from '@/store/action-types';

export default {
  name: 'license-filter',
  computed: {
    licenseTypes() {
      return this.$store.state.filters.licenseTypes;
    },
  },
  methods: {
    onFilterChanged(code) {
      this.$store.dispatch(TOGGLE_FILTER, {
        code,
        filterType: 'licenseTypes',
        shouldNavigate: false,
      });
    },
  },
};
</script>

<style lang="scss" scoped>
.home-license-filter {
  text-align: left;
  text-align: center;
}
span {
  display: block;
  font-size: 1.25em;
  font-weight: 600;
}
.license-filters {
  display: inline-block;
}
</style>
