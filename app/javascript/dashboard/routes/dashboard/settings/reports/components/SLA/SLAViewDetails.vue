<template>
  <div v-on-clickaway="closeSlaEvents" class="label-wrap">
    <div
      class="flex items-center col-span-2 px-0 py-2 text-sm tracking-[0.5] text-slate-700 dark:text-slate-100 rtl:text-right"
    >
      <div class="relative">
        <woot-button
          color-scheme="secondary"
          variant="link"
          @click="openSlaEvents"
        >
          {{ $t('SLA_REPORTS.TABLE.VIEW_DETAILS') }}
        </woot-button>
        <SLA-popover-card
          v-if="showSlaPopoverCard"
          :all-missed-slas="slaEvents"
          class="right-0"
        />
      </div>
    </div>
  </div>
</template>

<script>
import { mixin as clickaway } from 'vue-clickaway';
import SLAPopoverCard from 'dashboard/components/widgets/conversation/components/SLAPopoverCard.vue';
export default {
  components: {
    SLAPopoverCard,
  },
  mixins: [clickaway],

  props: {
    slaEvents: {
      type: Array,
      default: () => [],
    },
  },

  data() {
    return {
      showSlaPopoverCard: false,
    };
  },

  methods: {
    closeSlaEvents() {
      this.showSlaPopoverCard = false;
    },
    openSlaEvents() {
      this.showSlaPopoverCard = !this.showSlaPopoverCard;
    },
  },
};
</script>
