<template>
  <div id="form-edit" class="card mr-4">
    <form>
      <div class="card-header">
        <h3 class="text-dark">Edit Blogs</h3>
      </div>
      <div class="card-body">
        <div class="title">
          <h6>Tiêu đề</h6>
          <input class="width-input" type="input" v-model="listBlog.title" />
        </div>
        <div class="depcription mt-3">
          <h6>Mô tả ngắn</h6>
          <input
            id="input-depcription"
            class="width-input"
            type="input"
            v-model="listBlog.des"
          />
        </div>
        <div class="detail mt-3">
          <h6>Chi tiết</h6>
          <input
            id="input-detail"
            class="width-input"
            type="input"
            v-model="listBlog.detail"
          />
        </div>
        <div class="image mt-3">
          <h6>Hình ảnh:</h6>
          <input type="file" />
        </div>
        <div class="location mt-3">
          <h6>Vị trí:</h6>
          <ul class="list-location mt-2">
            <li class="new-select">
              <input type="checkbox" value="1" v-model="listBlog.position" />
              <label>Viet Nam</label>
            </li>

            <li class="new-select">
              <input type="checkbox" value="2" v-model="listBlog.position" />
              <label>Chau A</label>
            </li>

            <li class="new-select">
              <input type="checkbox" value="3" v-model="listBlog.position" />
              <label>Chau Au</label>
            </li>

            <li class="new-select">
              <input type="checkbox" value="4" v-model="listBlog.position" />
              <label>Chau My</label>
            </li>
          </ul>
        </div>
        <div class="public">
          <h6>Public</h6>
          <ul class="list-location mt-2">
            <li class="new-select">
              <input value="true" type="radio" v-model="listBlog.public" />
              <label>Yes</label>
            </li>

            <li class="new-select">
              <input value="false" type="radio" v-model="listBlog.public" />
              <label>No</label>
            </li>
          </ul>
        </div>
        <div class="row mt-3">
          <div class="cate col-md-6">
            <h6>Loại:</h6>
            <select
              class="width-input"
              name="select-cate"
              v-model="listBlog.category"
            >
              <option v-for="cate in cates" :key="cate.id">
                {{ cate.name }}
              </option>
            </select>
          </div>
          <div class="date col-md-6">
            <h6>Date public</h6>
            <input
              class="width-input"
              type="date"
              v-model="listBlog.data_pubblic"
            />
          </div>
        </div>
      </div>
      <div class="card-footer">
        <button type="button" class="btn btn-success" @click="update">
          Submit
        </button>
        <button type="button" class="btn btn-primary">Clear</button>
      </div>
    </form>
  </div>
</template>
<script>
import { API, CATEGORIES } from 'assets/constans'

export default {
  props: {
    idNew: String,
  },
  data() {
    return {
      cates: CATEGORIES,
      listBlog: {
        title: null,
        des: null,
        position: [],
        detail: null,
        data_pubblic: null,
        category: '',
        public: '',
      },
    }
  },
  mounted() {
    this.$axios.$get(API + this.idNew).then((res) => {
      this.listBlog = res
    })
  },
  validate() {},

  methods: {
    async update() {
      if (
        this.listBlog.title == null ||
        this.listBlog.depcription == null ||
        this.listBlog.detail == null
      ) {
        alert("Can't be left empty")
      }
      else{
        await this.$axios.$put(API + this.idNew, this.listBlog);
      }
    },
  },
}
</script>
<style>
#form-edit {
  margin-top: 90px;
}
.card-header {
  height: 50px;
}

.card-header h3 {
  margin-top: 2px;
  text-align: left;
}
.width-input {
  width: 98%;
  border-radius: 0, 7%;
}
#input-depcription {
  height: 150px;
}
#input-detail {
  height: 200px;
}
.new-select {
  display: inline-block;
}
.list-location {
  margin-left: -40px;
}
.cate select {
  height: 30px;
  border-width: thin;
  background-color: white;
}
.date input {
  width: 98%;
  border-radius: 0, 7%;
}
.card-footer {
  text-align: center;
}
</style>
