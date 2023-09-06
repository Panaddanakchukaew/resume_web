<!-- <template>
  <div class="section" data-theme="cupcake">
    <div class="flex h-screen">
      <div class="m-auto">
        <h1 class="text-6xl font-bold">RESUME</h1>
        <div class="hero-content flex-col lg:flex-row">
          <img src="./assets/img/download.jpg" class="max-w-sm rounded-lg shadow-2xl" />
          <div>
            <h1 class="text-5xl font-bold">Panadda Nakchukaew</h1>
            <p class="py-6">Hello, I am a student of information technology and digital innovation at Mahanakorn
              University of Technology.</p>

            <div class="tooltip tooltip-open tooltip-right" data-tip="hello">
              <button class="btn">Nan</button>
            </div>
          </div>
        </div>
        <ul class="menu xl:menu-horizontal lg:min-w-max bg-base-200 rounded-box">&emsp;&emsp;
          <li>
            <a>EDUCATION</a>
            <ul>
              <li><a>Mahanakorn University of Technology <br>
                  (2020 - Present)<br>
                  Bachelor of Science Information <br>
                  Technology and Digital Innovation<br>
                  GPA 3.15</a>
              </li>
            </ul>
          </li>
          <li>
            <a>CONTACT</a>
            <ul>
              <li><a>084-326-0583</a></li>
              <li><a>6314110019@mut.ac.th</a></li>
              <li><a>70/78 Sisa Chorakhe Noi, <br>Bang Sao Thong 10540</a></li>
            </ul>
          </li>
          <li>
            <a>SKILL</a>
            <ul>
              <li>
                <a>Hard Skills</a>
                <ul>
                  <li><a>MySQL</a></li>
                  <li><a>HTML</a></li>
                  <li><a>CSS</a></li>
                </ul>
                <a>Soft Skills</a>
                <ul>
                  <li><a>Work ethic</a></li>
                  <li><a>Teamwork</a></li>
                  <li><a>Problem-solving</a></li>
                </ul>
              </li>
            </ul>
          </li>
          <li>
            <a>LANGUAGE</a>
            <ul>
              <div class="radial-progress" style="--value:100;">Thai</div> &emsp; <div class="radial-progress"
                style="--value:50;">English</div> &emsp;&emsp;
            </ul>
          </li>
        </ul>
      </div>
    </div>
  </div>

  <div class="section" data-theme="halloween">

    <table class="table">
      <thead>
        <tr>
          <td>ID</td>
          <td>Product name</td>
          <td>Product price</td>
        </tr>
      </thead>
      <tbody>
        <tr class="hover" v-for="(product, index) in products" :key="index">
          <td>{{ index + 1 }}</td>
          <td>{{ product.name }}</td>
          <td>{{ product.price }}</td>
        </tr>
      </tbody>
    </table>

  </div>
</template>

<script setup>
import axios from 'axios';
import { ref, onMounted } from 'vue';
let products = ref()
onMounted(async () => {
  products.value = await getAllProduct();
  console.log(products);

})

const getAllProduct = async () => {
  let data = [];
  data = await axios.get('http://localhost:5000/getallproduct').then((Response) => {
    return Response.data;
  });  //สำคัญถ้าไม้ใส่http  ภาษาjs ? ใส่ก็ได้ไม่ใส่ก็ได้
  return data;
}

</script>

<style scoped>
.section {
  height: 100vh;
}
</style> -->



<template>
  <header>
    <div class="navbar bg-base-100">
      <div class="navbar-start">
        <div class="dropdown">
          <label tabindex="0" class="btn btn-ghost lg:hidden">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h8m-8 6h16" />
            </svg>
          </label>
          <ul tabindex="0" class="menu menu-sm dropdown-content mt-3 z-[1] p-2 shadow bg-base-100 rounded-box w-52">
            <li v-for="menu in menuList" :key="menu.name">
              <RouterLink :to="menu.path">{{ menu.name }}</RouterLink>
            </li>
          </ul>
        </div>
        <a class="btn btn-ghost normal-case text-xl">daisyUI</a>
      </div>
      <div class="navbar-center hidden lg:flex">
        <ul class="menu menu-horizontal px-1">
          <li v-for="menu in menuList" :key="menu.name">
            <RouterLink :to="menu.path">{{ menu.name }}</RouterLink>
          </li>
        </ul>
      </div>
      <!-- <div class="navbar-end">
          <a class="btn">Button</a>
        </div> -->
    </div>
  </header>
  <div class="container mx-auto">
    <RouterView :key="router.currentRoute.value.name"/>
  </div>
</template>

<script setup>
import { RouterView, RouterLink } from 'vue-router';
import router from './router';
const menuList = [
  { path: "/", name: "home" },
  { path: "/create", name: "create" },
]

</script>

<style scoped></style>