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
          <div
            v-for="(position, index) in posis"
            :key="index"
            class="form-check form-check-inline"
          >
            <input
              class="form-check-input"
              v-model="posts.position"
              type="checkbox"
              :value="position.id"
            /><label class="position">{{ position.name }}</label>
          </div>
        </div>
        <div class="public mt-3">
          <h6>Public</h6>
          <ul class="list-location mt-2">
            <li class="new-select">
              <input value="1" type="radio" v-model="posts.public" />
              <label>Yes</label>
            </li>

            <li class="new-select">
              <input value="0" type="radio" v-model="posts.public" />
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
              v-model="posts.category"
            >
              <option v-for="cate in cates" :key="cate.id" :value="cate.id">
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
        <button type="button" class="btn btn-success" @click="onSubmit">
          Submit
        </button>
        <button type="button" class="btn btn-primary">Clear</button>
      </div>
    </form>
  </div>
</template>
<script>
import { API, CATEGORIES, POSITIONS } from 'assets/constans'
import axios from 'axios'
export default {
  props: {
    idNew: String,
    flagCheckisCreate : Number
  },
  data() {
    return {
      posis: POSITIONS,
      cates: CATEGORIES,
      listBlog: [],
      posts: {
        title: null,
        des: null,
        detail: null,
        category: null,
        public: null,
        data_pubblic: null,
        position: [],
        thumbs: 'fwefwe',
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
        alert("Not be empty ")
        
        return false
      }
      return true
    },
    async onSubmit() {
      if (this.validate()) {
        if (this.flagCheckisCreate == 1) {
          let temp = this.posts.position[0]
          this.posts.position = temp
          axios.post(API, this.posts)
        } else {
          let temp = this.posts.position[0]
          this.posts.position = temp
          axios.put(API + '/' + this.idNew, this.posts)
        }
      }
    },
  },
  mounted() {
    if (this.flagCheckisCreate !== 1) {
      axios.get(API + '/' + this.idNew).then((response) => {
        this.posts = response.data.data[0]
        let temp = this.posts.position
        this.posts.position = [temp]
      })
    }
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

.position {
  margin-bottom: 0.1rem;
}
.card-footer {
  text-align: center;
}
</style>
