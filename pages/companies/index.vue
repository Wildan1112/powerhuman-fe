<template>
  <section class="py-[200px] flex flex-col items-center justify-center px-4">
    <div class="font-semibold text-dark mb-4 text-[32px]">Select Companies</div>
    <form class="w-full card">
      <div class="form-group">
        <label for="" class="text-gray">Companies</label>
        <select name="" id="" class="appearance-none input-field form-icon-chevron-down">
          <option value="" selected>Company Name</option>
        </select>
      </div>
      <a href="" class="w-full btn btn-primary mt-[14px]">Continue</a>
    </form>
  </section>
</template>

<script>
export default {
  middleware: 'auth'
}
</script>
