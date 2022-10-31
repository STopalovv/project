<template>
  <v-app>
    <div class="superior">
      <form-component />
      <form-content class="form-content-view" />
      <analyst-ratings />
      <financial-reports class="finacial-reports" />
      <page-footer class="footer" />
    </div>
  </v-app>
</template>

<script>
import AnalystRatings from '~/components/AnalystRatings.vue'
import FinancialReports from '~/components/FinancialReports.vue'
import FormContent from '~/components/FormContent.vue'
import FormComponent from '~/components/FormComponent.vue'
import PageFooter from '~/components/PageFooter.vue'
export default {
  components: { AnalystRatings, FinancialReports, PageFooter, FormComponent, FormContent }
}
</script>

<style>
.footer {
        margin-top: 4%;
    }
    @media only screen and (min-width: 700px) {
        .superior {
            position: relative;
        }
        .form-content-view {
            position: absolute;
            top: 4%;
            right: 10%;
            width: 30vw;
        }
    }
</style>
