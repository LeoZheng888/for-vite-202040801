<script setup>
import { ref } from 'vue';
/* const text = ref('這是一段文字');
const city = ref('台北市')
const isCheck = ref(true)
const arrayCheckbox = ref([])
const radioValue = ref('男')

const num = ref(2);
function clickMe() {
  num.value++
} */
/* let num = ref(0)
const htmlTemplate = `<h1>這是 HTML 片段 </h1>`
setInterval(() => {
  num.value++
}, 500); */

/* const imgUrl = ref('https://plus.unsplash.com/premium_photo-1722170080353-5b68cd7b16ff?q=80&w=600&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D')
const isChecked = ref(false) */

/* const handleClick = () => {
  console.log('我被觸發了');
}
const submitForm = () => {
  console.log('表單被觸發了')
} */

/* const array = ref([
  {
    id: '1',
    name: '小明',
    age: 18
  },
  {
    id: '2',
    name: '小美',
    age: 16
  },
  {
    id: '3',
    name: '漂亮阿姨',
    age: 20
  }])

const isChecked = ref(false);
 */


const data = ref([{
  id: '1',
  name: '珍珠奶茶',
  describe: '香濃奶茶搭配QQ珍珠',
  price: 50,
  inventory: 20,
  edit: false,
  tempName: ''
},
{
  id: '2',
  name: '冬瓜檸檬',
  describe: '清新冬瓜配上新鮮檸檬',
  price: 45,
  inventory: 18,
  edit: false,
  tempName: ''
}, {
  id: '3',
  name: '翡翠檸檬',
  describe: '綠茶與檸檬的完美結合',
  price: 55,
  inventory: 34,
  edit: false,
  tempName: ''
},
{
  id: '4',
  name: '四季春茶',
  describe: '香醇四季春茶，回甘無比',
  price: 45,
  inventory: 10,
  edit: false,
  tempName: ''
},
{
  id: '5',
  name: '阿薩姆奶茶',
  describe: '阿薩姆紅茶搭配香醇鮮奶',
  price: 50,
  inventory: 25,
  edit: false,
  tempName: ''
},
{
  id: '6',
  name: '檸檬冰茶',
  describe: '檸檬與冰茶的清新組合',
  price: 45,
  inventory: 20,
  edit: false,
  tempName: ''
},
{
  id: '7',
  name: '芒果綠茶',
  describe: '芒果與綠茶的獨特風味',
  price: 55,
  inventory: 18,
  edit: false,
  tempName: ''
},
{
  id: '8',
  name: '抹茶拿鐵',
  describe: '抹茶與鮮奶的絕配',
  price: 60,
  inventory: 20,
  edit: false,
  tempName: ''
}
])



function Reduce(num, key) {
  if (num.inventory == 0) {
    return
  }
  if (num.id - 1 == key) {
    num.inventory--
  }
}
function Add(num, key) {
  if (num.id - 1 == key) {
    num.inventory++
  }
}
const isChecked = ref(false)

function isCheck(item, key) {

  if (item.id - 1 == key) {
    item.tempName = item.name
    item.edit = true
  }

}

function saveName(item, key) {
  if (item.id - 1 == key) {
    item.name = item.tempName
  }
  item.edit = false
}

function cancleEdit(item, key) {


  if (item.id - 1 == key) {
    item.tempName = item.name;
    item.edit = false
  }
}

</script>

<!-- <style>
.box {
  height: 100px;
  width: 100px;
  background-color: red;
  transition: .5s all;
}

.rotate {
  transform: rotate(45deg) 
}
</style> -->

<template>
  <table>
    <thead>
      <tr>
        <th scope="col">品項</th>
        <th scope="col">描述</th>
        <th scope="col">價格</th>
        <th scope="col">庫存</th>
        <th scope="col">編輯品項</th>
      </tr>
    </thead>
    <tbody v-for="(item, key) in data" :key="item.id">
      <tr>
        <td style="width: 100px;">{{ item.name }}
          <!--   <input type="text" v-model="item.name" v-if="item.edit">
          <button type="button" v-if="item.edit">儲存</button>
          <button type="button" v-if="item.edit">取消</button> -->
        </td>
        <td style="width: 150px; text-align: center;"><small>{{ item.describe }}</small></td>
        <td style="width: 50px; text-align: center;">{{ item.price }}</td>
        <td><button type="button" @click="Reduce(item, key)">-</button>
          {{ item.inventory }}
          <button type="button" @click="Add(item, key)">+</button>
        </td>
        <td>
          <button style="width: 50px; text-align: center;" type="button" @click="isCheck(item, key)">編輯</button>
          <input type="text" v-model="item.tempName" v-if="item.edit">
          <button type="button" v-if="item.edit" @click="saveName(item, key)">儲存</button>
          <button type="button" v-if="item.edit" @click="cancleEdit(item, key)">取消</button>
        </td>
      </tr>
    </tbody>
  </table>
  <!--   <div>
    <div>
      姓名:{{ array[0].name }}
      年齡: {{ array[0].age }}
    </div>
    <div v-for="(item, key) in array" :key="item.id">
      索引:{{ key }}
      姓名:{{ item.name }}
      年齡:{{ item.age }}
    </div>
    <hr>
    <input type="checkbox" v-model="isChecked">{{ isChecked }}
    <h1 v-if="isChecked">當 isChecked ==true 的時候會顯示</h1>
    <h1 v-else="isChecked">目前 isChecked ==FALSE</h1>
  </div> -->


  <!-- <div>
    <br><br><br><br><br><br><br><br><br><br>
    <form @submit="submitForm">
      <button type="button" @click="handleClick">點我</button>
      <button type="submit.prevent">點我</button>
    </form>
    <h2>事件修飾符</h2>
    <a href="#" @click.prevent="handleChick">點我R</a>

    <h2>按鍵修飾符</h2>
    <input type="text" v-on:keydown.enter="handleClick">

  </div> -->

  <!--  <div>
    <img :src="imgUrl" alt="">
    <h2>可以套用在任何屬性上</h2>
    {{ isChecked }}
    <input type="checkbox" v-model="isChecked">
    <input type="text" :disabled="isChecked">
    <h2>可以套用在行內樣式上</h2>
    <div class="box" :style="{ transform: isChecked ? 'rotate(45deg)' : null }"></div>
    <div class="box" :style="{ backgroundColor: isChecked ? 'red' : 'green' }"></div>

    <h2>class</h2>
    <div class="box" :class="{ rotate: isChecked }"></div>
  </div> -->
  <!-- <div>
    <h1>這個數值目前是：{{ num }}</h1>
  </div>
  <div v-html="htmlTemplate"></div> -->
  <!--  <div>
    {{ num }}
    <button type="button" v-on:click="clickMe">點我阿</button>

    <h1>{{ text }}</h1>

    <input type="text" v-model="text">
    {{ city }}
    <select name="" id="" v-model="city">
      <option value="台北市">台北市</option>
      <option value="台中市">台中市</option>
      <option value="桃園市">桃園市</option>
    </select>
    <hr>
    {{ isCheck }}
    <input type="checkbox" v-model="isCheck">
    <hr>
    {{ arrayCheckbox }}
    <input type="checkbox" v-model="arrayCheckbox" value="漂亮阿姨">
    <input type="checkbox" v-model="arrayCheckbox" value="小明">
    <input type="checkbox" v-model="arrayCheckbox" value="杰倫">

    <hr>

    {{ radioValue }}
    <input type="radio" v-model="radioValue" value="男">
    <input type="radio" v-model="radioValue" value="女">
  </div> -->
</template>
