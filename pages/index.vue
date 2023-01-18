<template>
  <section class="py-[200px] flex flex-col items-center justify-center px-4">
    <div class="font-semibold text-dark mb-4 text-[32px]">Select Companies</div>
    <div class="w-full card">
      <div class="form-group">
        <label for="" class="text-gray">Companies</label>
        <p v-if="$fetchState.pending">Fetch Companies</p>
        <select v-if="companies.data" v-model="selectedCompany" name="companies"
          class="appearance-none input-field form-icon-chevron-down">
          <option :value="company.id" v-for="company in companies.data.result.data">
            {{ company.name }}
          </option>
        </select>
      </div>
      <button @click="openCompany()" type="button" class="w-full btn btn-primary mt-[14px]">Continue</button>
      <p class="flex items-center justify-center">Or</p>
      <NuxtLink :to="{name: 'companies-create'}" class="w-full text-black transition duration-300 btn btn-primary bg-slate-100 hover:bg-slate-200">Add New Company</NuxtLink>
    </div>
  </section>
</template>

<script>
export default {
  middleware: 'auth',
  data() {
    return {
      companies: [],
      selectedCompany: '',
    }
  },
  async fetch() {
    this.companies = await this.$axios.get('/company?limit=100')
  },
  methods: {
    openCompany() {
      this.$router.push({
        name: 'companies-id',
        params: {
          id: this.selectedCompany,
        }
      })
    }
  },
}
</script>
