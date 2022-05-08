<template>
  <pilot-header/>
  <pilot-campaign/>
  <automation-flow/>
</template>

<script>
import PilotHeader from './components/PilotHeader'
import PilotCampaign from './components/PilotCampaign'
import AutomationFlow from './components/AutomationFlow'
export default {
  name: 'App',
  components: {
    PilotHeader,
    PilotCampaign,
    AutomationFlow
  }
}
</script>

<style lang="css">
</style>
