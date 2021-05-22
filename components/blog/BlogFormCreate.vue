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
          <input id="input-depcription" class="width-input" type="input" v-model="posts.depcription" />
        </div>
        <div class="detail mt-3">
          <h6>Chi tiết</h6>
          <input id="input-detail" class="width-input" type="input" v-model="posts.detail" />
        </div>
        <div class="image mt-3">
          <h6>Hình ảnh:</h6>
          <input type="file"/>
        </div>
        <div class="location mt-3">
          <h6>Vị trí:</h6>
          <ul class="list-location mt-2">
            <li class="new-select">
              <input class="any" id="any" name="any" type="checkbox" v-model="posts.checked" />
              <label id="any" for="any">Viet Nam</label>
            </li>

            <li class="new-select">
              <input id="item1" name="item1" type="checkbox" v-model="posts.checked" />
              <label id="item1" for="item1">Chau A</label>
            </li>

            <li class="new-select">
              <input id="item2" name="item2" type="checkbox" v-model="posts.checked" />
              <label id="item2" for="item2">Chau Au</label>
            </li>

            <li class="new-select">
              <input id="item3" name="item3" type="checkbox" v-model="posts.checked"/>
              <label id="item3" for="item3">Chau My</label>
            </li>
          </ul>
        </div>
        <div class="public">
          <h6>Public</h6>
          <ul class="list-location mt-2">
            <li class="new-select">
              <input class="any" id="any" name="any" value="Yes" type="radio" v-model="posts.picked"/>
              <label id="any" for="any">Yes</label>
            </li>

            <li class="new-select">
              <input id="item1" name="item1" type="radio" v-model="posts.picked" />
              <label id="item1" for="item1">No</label>
            </li>
          </ul>
        </div>
        <div class="row mt-3">
          <div class="cate col-md-6">
            <h6>Loại:</h6>
            <select
              class="width-input"
              name="select-cate">
              <option v-for="cate in cates" :key="cate.id" v-bind:cate="cate">
                {{ cate.name }}
              </option>
            </select>
          </div>
          <div class="date col-md-6">
            <h6>Date public</h6>
            <input
              class="width-input"
              type="date"
              id="birthday"
              name="birthday"
            />
          </div>
        </div>
      </div>
      <div class="card-footer">
        <button type="button" class="btn btn-success" @click="postData">Submit</button>
        <button type="button" class="btn btn-primary">Clear</button>
      </div>
    </form>
  </div>
</template>
<script>
import { CATEGORIES } from 'assets/constans';
export default {
  data(){
    return{
      cates : CATEGORIES,
      posts :{
        title : null,
        depcription :null,
        checked :null,
        detail : null,
      }
    }
  },
  methods:{
    postData(e){
      console.log(this.posts);
      console.log("hihi");
    }
  }
}
</script>
<style>
.card-header{
  height: 50px;
}

.card-header h3{
  margin-top: 2px;
  text-align: left;
}

#form-create {
  z-index: 2;
  position: relative;
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
