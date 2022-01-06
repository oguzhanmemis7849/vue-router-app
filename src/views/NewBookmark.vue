<template>
  <div class="card p-2">
    <div class="mb-3">
      <label for="title" class="form-label" id="title">Başlık</label>
      <input
        type="text"
        v-model="userData.title"
        class="form-control"
        id="exampleFormControlInput1"
        placeholder="Aramak istediğinizi yazınız."
      />
    </div>
    <div class="mb-3">
      <label for="url" class="form-label" id="url">URL</label>
      <input
        type="text"
        v-model="userData.url"
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
        v-model="userData.description"
        class="form-control"
        placeholder="Bu var ya..."
        id="dexcription"
        rows="3"
      ></textarea>
    </div>
    <!-- @click="$router.go(-1)" bir önceki sayfaya gider -->
    <div class="d-flex justify-content-end align-items-center">
      <button class="btn btn-sm btn-secondary me-1" @click="$router.push({ name : 'HomePage' })">İptal</button>
      <button class="btn btn-sm btn-primary" @click="onSave">Kaydet</button>
    </div>
  </div>
</template>

<script>
export default {
  data(){
    return {
      userData : {
        title : null,
        url : null,
        description : null
      }
    }
  },
  methods: {
    onSave(){
      console.log(this.userData);
      this.$appAxios.post("/bookmarks", this.userData).then(save_response => {
        console.log("save_response", save_response);
        this.resetData();
        this.$router.push("/"); //kaydet butonundan sonra anasayfa yönlendirmesi
      });
    },
    //New alanının inputlarını ve textarea'yı temizler
    resetData(){
      Object.keys(this.userData).forEach(key => (this.userData[key] = null));
    }
  }
};
</script>

<style></style>
