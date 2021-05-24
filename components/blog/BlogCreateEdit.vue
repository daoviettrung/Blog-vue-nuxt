<template>
  <div id="form-create" class="card mr-4">
    <form>
      <div class="card-header">
        <h3 class="text-dark">New Blogs</h3>
      </div>
      <div class="card-body">
        <div class="title">
          <h6>Tiêu đề</h6>
          <input class="width-input" type="input" v-model="posts.title" />
        </div>
        <div class="depcription mt-3">
          <h6>Mô tả ngắn</h6>
          <input
            id="input-depcription"
            class="width-input"
            type="input"
            v-model="posts.des"
          />
        </div>
        <div class="detail mt-3">
          <h6>Chi tiết</h6>
          <input
            id="input-detail"
            class="width-input"
            type="input"
            v-model="posts.detail"
          />
        </div>
        <div class="image mt-3">
          <h6>Hình ảnh:</h6>
          <input type="file" />
        </div>
        <div class="location mt-3">
          <h6>Vị trí:</h6>
          <ul class="list-location mt-2">
            <li
              v-for="(position, index) in posis"
              :key="index"
              class="new-select"
            >
              <input
                style="margin-left: 10px"
                :id="position.id"
                type="checkbox"
                :value="position.id"
                v-model="posts.position"
              />
              <label>{{ position.name }}</label>
            </li>
          </ul>
        </div>
        <div class="public">
          <h6>Public</h6>
          <ul class="list-location mt-2">
            <li class="new-select">
              <input value="true" type="radio" v-model="posts.public" />
              <label>Yes</label>
            </li>

            <li class="new-select">
              <input value="false" type="radio" v-model="posts.public" />
              <label>No</label>
            </li>
          </ul>
        </div>
        <div class="row mt-3">
          <div class="cate col-md-6">
            <h6>Loại:</h6>
            <select class="width-input" name="select-cate" v-model="posts.cate">
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
              v-model="posts.data_pubblic"
            />
          </div>
        </div>
      </div>
      <div class="card-footer">
        <button type="button" class="btn btn-success" @click="postData">
          Submit
        </button>
        <button type="button" class="btn btn-primary">Clear</button>
      </div>
    </form>
  </div>
</template>
<script>
import { API, CATEGORIES, POSITIONS } from 'assets/constans'
export default {
  async fetch() {
    this.listBlog = await fetch(API).then((res) => res.json())
  },
  props: {
    idNew: String,
  },
  data() {
    return {
      posis: POSITIONS,
      cates: CATEGORIES,
      listBlog: [],
      posts: {
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

  methods: {
    validate() {
      if (
        this.posts.title == null ||
        this.posts.des == null ||
        this.posts.detail == null
      ) {
        alert("Can't be left empty")
        return false
      }
      return true
    },
    async postData() {
      if (this.validate()) {
        if ((this.idNew != "")) {
          var idCate
          CATEGORIES.forEach((value) => {
            if (value.name == this.posts.cate) {
              idCate = value.id
            }
          })
          var max = 0
          this.listBlog.forEach((value) => {
            if (value.id > max) {
              max = value.id
            }
          })
          this.$axios
            .post(API, {
              id: max + 1,
              title: this.posts.title,
              des: this.posts.des,
              detail: this.posts.detail,
              category: idCate,
              public: this.posts.public,
              data_pubblic: this.posts.data_pubblic,
              position: this.posts.position,
            })
            .then(function (response) {
              console.log(response)
            })
            .catch(function (error) {
              console.log(error)
            })
        } else {
          await this.$axios.$put(API + this.idNew, this.posts)
        }
      }
    },
  },

  mounted() {
    this.$axios.$get(API + this.idNew).then((res) => {
      this.posts = res
    })
  },
}
</script>
<style>
.card-header {
  height: 50px;
}

.card-header h3 {
  margin-top: 2px;
  text-align: left;
}

#form-create {
  margin-top: 90px;
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

