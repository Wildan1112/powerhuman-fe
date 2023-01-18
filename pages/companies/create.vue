<template>
  <section class="py-[200px] flex flex-col items-center justify-center px-4">
    <div class="font-semibold text-dark mb-4 text-[32px]">Add Companies</div>
    <form class="w-full card" @submit.prevent="addCompany()">
      <div class="form-group">
        <label for="" class="text-grey">Company Name</label>
        <input type="text" class="input-field" v-model="company.name" name="name" />
      </div>

      <button type="submit" class="w-full btn btn-primary mt-[14px]">
        Add Company
      </button>
    </form>
  </section>
</template>

<script>
export default {
  middleware: 'auth',
  data() {
    return {
      company: {
        name:''
      }
    }
  },
 methods: {
  async addCompany() {
   try {
    this.$axios.post('/company', this.company)
      .then(response => {
        this.$router.push({
          name: 'companies-id',
          params: {
            id: response.data.result.id,
          }
        })
      })

   } catch (error) {
    console.log(error);
   }
  }
 }
}
</script>
