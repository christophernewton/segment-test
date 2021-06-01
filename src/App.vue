<template>
  <section>
    <form @submit.prevent="sendData">
      email<input type="text" v-model="form.email" /><br />
      firstName<input type="text" v-model="form.firstName" /><br />
      lastName<input type="text" v-model="form.lastName" /><br />
      comments<input type="text" v-model="form.comments" /><br />
      consent<input type="text" v-model="form.consent" /><br />
      country<input type="text" v-model="form.country" /><br />
      enquiryType<input type="text" v-model="form.enquiryType" /><br />
      formAssetId<input type="text" v-model="form.formAssetId" /><br />
      formName<input type="text" v-model="form.formName" /><br />
      industry<input type="text" v-model="form.industry" /><br />
      jobTitle<input type="text" v-model="form.jobTitle" /><br />
      organisation<input type="text" v-model="form.organisation" /><br />
      pageAssetId<input type="text" v-model="form.pageAssetId" /><br />
      phone<input type="text" v-model="form.phone" /><br />
      referrer<input type="text" v-model="form.referrer" /><br />
      search<input type="text" v-model="form.search" /><br />
      title<input type="text" v-model="form.title" /><br />
      url<input type="text" v-model="form.url" /><br />
      userAgent<input type="text" v-model="form.userAgent" /><br />
      <button>SUBMIT</button>
    </form>
    <pre>{{form}}</pre>
  </section>
</template>

<script>
import {ref, onMounted} from 'vue'
export default {
  setup() {
    const form = ref({
      comments: "Comment test",
      consent: "yes",
      country: "Australia",
      email: `test${(Math.random() * 10000).toFixed(0)}@test.com`,
      enquiryType: "sales",
      firstName: `FNAME${(Math.random() * 10000).toFixed(0)}`,
      formAssetId: "117597",
      formName: "contact us - SALES",
      industry: "Other",
      jobTitle: "Mr",
      lastName: `LASTNAME${(Math.random() * 10000).toFixed(0)}`,
      organisation: `ORG-${(Math.random() * 10000).toFixed(0)}`,
      pageAssetId: "116728",
      phone: "0431000000",
      referrer: "https://technologyonecorp.com/",
      search: "",
      title: "Contact us",
      url: "https://technologyonecorp.com/company/contact-us",
      userAgent: window.navigator.userAgent
    })
    const sendData = () => {
      /* console.log('sending identify')
      analytics.identify(
        form.value,
        {
          integrations: {
            Marketo: true,
          },
        }
      )
      console.log('finished identify') */
      console.log('sending track')
      analytics.track('contact us', {
        phone: form.value.phone,
        firstName: form.value.firstName,
        lastName: form.value.lastName,
        email: form.value.email,
        jobTitle: form.value.jobTitle,
        organisation: form.value.organisation,
        country: form.value.country,
        industry: form.value.industry,
        enquiryType: form.value.enquiryType,
        formAssetId: form.value.formAssetId,
        category: form.value.category,
        label: form.value.label,
        formName: form.value.formName,
        consent: form.value.consent,
        comments: form.value.comments,
        url: form.value.url,
        path: form.value.path,
        pageAssetId: form.value.pageAssetId,
        title: form.value.title,
        search: form.value.search,
        referrer: form.value.referrer,
        userAgent: form.value.userAgent,
      });
      console.log('finished track')

    }
    return {
      sendData,
      form
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
pre {
  text-align: left;
}
</style>
