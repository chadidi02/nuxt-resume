<template>
  <div class="my-auto">
    <h2 class="mb-5">{{ $t('work') }}</h2>

    <div
      v-for="(work, index) in workExperiences"
      :key="index"
      class="resume-item d-flex flex-column flex-md-row mb-5"
    >
      <div class="resume-content mr-auto">
        <h3 class="mb-0">{{ work.position }}</h3>
        <div class="subheading mb-3">{{ work.company }}</div>
        <p>{{ work.summary }}</p>
        <p
          v-for="highlights in work.highlights"
          :key="highlights"
        >
          - {{ highlights }}
        </p>
      </div>
      <div class="resume-date text-md-right">
        <span class="text-primary">{{ work.startDate }} - {{ work.endDate || $t('present') }}</span>
      </div>
    </div>
  </div>
</template>

<script>
import { mapState } from 'vuex'

export default {
  computed: {
    ... mapState({
      workExperiences: state => state.resume.work
    }),
  }
};
</script>
