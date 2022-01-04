<template>
  <div class="form-area card border p-2">
    <div class="mb-3">
      <label for="title" class="form-label" id="title">Başlık</label>
      <input
        type="text"
        class="form-control"
        id="exampleFormControlInput1"
        placeholder="Aramak istediğinizi yazınız."
      />
    </div>
    <div class="mb-3">
      <label for="url" class="form-label" id="url">URL</label>
      <input
        type="text"
        class="form-control"
        id="exampleFormControlInput1"
        placeholder="https://..."
      />
    </div>
    <div class="mb-3">
      <label for="description" class="form-label" id="description"
        >Açıklama</label
      >
      <textarea
        class="form-control"
        placeholder="Bu var ya..."
        id="dexcription"
        rows="3"
      ></textarea>
    </div>
    <div class="d-flex justify-content-end align-items-center">
      <button class="btn btn-sm btn-secondary me-1" @click="$router.push({ name : 'HomePage' })">İptal</button>
      <button class="btn btn-sm btn-primary">Kaydet</button>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style></style>
