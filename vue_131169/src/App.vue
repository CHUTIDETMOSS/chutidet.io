<script setup lang="ts">
import { ref } from 'vue'
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'
import TestPage from './components/TestPage.vue'
import MyNameIs from './components/MyNameIs.vue' // ✅ เพิ่มบรรทัดนี้
import Calculator from './components/calculator.vue' // ✅ เพิ่มบรรทัดนี้

const currentPage = ref<'home' | 'test' | 'about' | 'calculator'>('home') // ✅ เพิ่ม 'about' และ 'calculator'
</script>

<template>
  <header>
    <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />
    <div class="wrapper">
      <HelloWorld msg="You did it!" />
      <nav class="menu">
        <button @click="currentPage = 'home'">หน้าหลัก</button>
        <button @click="currentPage = 'test'">หน้าทดสอบใหม่</button>
        <button @click="currentPage = 'about'">แนะนำตัว</button> <!-- ✅ เพิ่มปุ่มเมนู -->
        <button @click="currentPage = 'calculator'">เครื่องคิดเลข</button> <!-- ✅ เพิ่มปุ่มเมนู -->
      </nav>
    </div>
  </header>

  <main>
    <TheWelcome v-if="currentPage === 'home'" />
    <TestPage v-if="currentPage === 'test'" />
    <MyNameIs v-if="currentPage === 'about'" /> <!-- ✅ เพิ่มส่วนแสดงผล -->
    <Calculator v-if="currentPage === 'calculator'" /> <!-- ✅ เพิ่มส่วนแสดงผล -->
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

/* ปรับสไตล์ปุ่มเมนูให้ดูสวยขึ้นเล็กน้อย */
.menu {
  display: flex;
  gap: 0.75rem;
  flex-wrap: wrap;
  margin-top: 1rem;
}

.menu button {
  padding: 0.5rem 1rem;
  border: 1px solid #3b82f6;
  background-color: #fff;
  color: #3b82f6;
  border-radius: 6px;
  cursor: pointer;
  transition: all 0.2s;
}

.menu button:hover {
  background-color: #3b82f6;
  color: #fff;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
