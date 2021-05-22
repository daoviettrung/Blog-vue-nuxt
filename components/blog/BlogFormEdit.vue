<template>
  <div id="form-create" class="card mr-4">
    <div class="card-header">
      <h3>Edit BLog</h3>
    </div>
    <div class="card-body">
      <div class="title">
        <h6>Tiêu đề</h6>
        <input class="width-input" type="input" />
      </div>
      <div class="depcription mt-3">
        <h6>Mô tả ngắn</h6>
        <input id="input-depcription" class="width-input" type="input" />
      </div>
      <div class="detail mt-3">
        <h6>Chi tiết</h6>
        <input id="input-detail" class="width-input" type="input" />
      </div>
      <div class="image mt-3">
        <h6>Hình ảnh:</h6>
        <input type="file" />
      </div>
      <div class="location mt-3">
        <h6>Vị trí:</h6>
        <ul class="list-location mt-2">
          <li class="new-select">
            <input class="any" id="any" name="any" type="checkbox" />
            <label id="any" for="any">Viet Nam</label>
          </li>

          <li class="new-select">
            <input id="item1" name="item1" type="checkbox" />
            <label id="item1" for="item1">Chau A</label>
          </li>

          <li class="new-select">
            <input id="item2" name="item2" type="checkbox" />
            <label id="item2" for="item2">Chau Au</label>
          </li>

          <li class="new-select">
            <input id="item3" name="item3" type="checkbox" />
            <label id="item3" for="item3">Chau My</label>
          </li>
        </ul>
      </div>
      <div class="public">
        <h6>Public</h6>
        <ul class="list-location mt-2">
          <li class="new-select">
            <input class="any" id="any" name="any" type="radio" />
            <label id="any" for="any">Yes</label>
          </li>

          <li class="new-select">
            <input id="item1" name="item1" type="radio" />
            <label id="item1" for="item1">No</label>
          </li>
        </ul>
      </div>
      <div class="row mt-3">
        <div class="cate col-md-6">
          <h6>Loại:</h6>
          <select class="width-input" name="select-cate" aria-placeholder="Chooce...">
            <option value="volvo">Chooce...</option>
          </select>
        </div>
        <div class="date col-md-6">
            <h6>Date public</h6>
             <input class="width-input" type="date" id="birthday" name="birthday">
        </div>
      </div>
    </div>
    <div class="card-footer">
      <button type="button" class="btn btn-success">Submit</button>
      <button type="button" class="btn btn-primary">Clear</button>
    </div>
  </div>
</template>
<style>
#form-create{
    z-index: 2;
    position: relative;
}
.width-input {
  width: 98%;
  border-radius: 0,7%;
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
 .cate select{
   height: 30px;
  border-width: thin;
  background-color: white;
} 
.date input{
  width: 98% ;
  border-radius: 0,7%;
}
.card-footer{
    text-align: center;
}
</style>
